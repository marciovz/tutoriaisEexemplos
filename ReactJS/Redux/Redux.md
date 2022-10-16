# Redux

### Instalar as bibliotecas
```cmd
$ npm install redux react-redux
```

### Implementando o index.js do store
src/store/index.js
```js 
  import { createStore } from 'redux';
  import rootReducer from './modules/rootReducer';
  const store = createStore(rootReducer);
  export default store;
```

### Implementando o arquivo rootReducer
src/store/modules/rootReducer.js
```js
  import { combineReducers } from 'redux';

  import cart from './cart/reducer';

  export default combineReducers({ cart });
```

### implementando o arquivo action.js
src/store/modules/cart/reducer.js
```js
  export function addToCart(product) {
    return {
      type: '@cart/ADD',
      product,
    };
  }

  export function removeFromCart(id) {
    return {
      type: '@cart/REMOVE',
      id,
    };
  }
```

### Implementando o arquivo reducer.js
src/store/modules/cart/reducer.js
```js
  export default function cart(state = {}, action) {
    switch (action.type) {
      case 'ADD_TO_CART':
        return [...state, action.product];
      default:
        return state;
    }
  }
```

### Implementando o arquivo App.js
src/app.js
```js
  . . . 
  import { Provider } from 'react-redux';

  import store from './store';
  . . . 
  export default function App() {
    return (
      <Provider store={store}>
        <BrowserRouter>
          <Header />
          <Routes />
          <GlobalStyle />
        </BrowserRouter>
      </Provider>
    );
  }
```

### Implementando o página Home
src/pages/Home.js
```js
  import { connect } from 'react-redux';
  import { bindActionCreators } from 'redux';
  import * as CartActions from '../../store/modules/cart/actions';

  const Home = () => {
    . . . 
    handleAddProduct = product => {
      const { addToCart } = this.props;
      addToCart(product);
    };

    render() {
      <button
        type="button"
        onClick={() => this.handleAddProduct(product)}
      >
      . . . 
    }
  }
  
  const mapDispatchToProps = dispatch => bindActionCreators(CartActions, dispatch);

  export default connect(null, mapDispatchToProps)(Home);
```


### Implentando o arquivo Header.js
src/components/Header.js
```js 
  import { connect } from 'react-redux';

  . . . 

  function Header({ cartSize }) {
    . . . 
    <span>{ cartSize } itens</span>
    . . . 
  }

  export default connect(state => ({
    cartSize: state.cart.length;
  }))(Header);
```

