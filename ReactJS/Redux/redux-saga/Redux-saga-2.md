# Redux Saga

### Instalando a biblioteca redux-saga
```cmd
$ npm install redux-saga
```


### Implementando o arquivo saga.js
src/store/cart/saga.js
```js
  import { call, put, all, takeLatest } from 'redux-saga/effects';

  import api from '../../../services/api';

  import { addToCartSuccess } from './actions';

  function* addToCart({ id }) {
    const response = yield call(api.get, `/products/${id}`);

    yield put(addToCartSuccess(response.data));
  }

  export default all([takeLatest('@cart/ADD_REQUEST', addToCart)]);
```


### Implementando o arquivo action.js
src/store/cart/action.js
```js
  export function addToCartRequest(id) {
    return {
      type: '@cart/ADD_REQUEST',
      id,
    };
  }

  export function addToCartSuccess(product) {
    return {
      type: '@cart/ADD_SUCCESS',
      product,
    };
  }
```


### Implementando o arquivo reducer.js
src/store/cart/reducer.js
```js
  . . . 
  export default function cart(state = [], action) {
    switch (action.type) {
      case '@cart/ADD_SUCCESS':
        return produce(state, draft => {
          const productIndex = draft.findIndex(p => p.id === action.product.id);
  . . . 
```


### Implementando o arquivo rootSaga.js
src/store/cart/rootSaga.js
```js
  import { all } from 'redux-saga/effects';

  import cart from './cart/sagas';

  export default function* rootSaga() {
    return yield all([cart]);
  }
```


### Implementando o arquivo rootSaga.js
src/store/index.js
```js
  import { createStore, applyMiddleware, compose } from 'redux';
  import createSagaMiddleware from 'redux-saga';

  import rootReducer from './modules/rootReducer';
  import rootSaga from './modules/rootSaga';

  const sagaMiddleware = createSagaMiddleware();

  const enhancer =
    process.env.NODE_ENV === 'development'
      ? compose(console.tron.createEnhancer(), applyMiddleware(sagaMiddleware))
      : applyMiddleware(sagaMiddleware);

  const store = createStore(rootReducer, enhancer);

  sagaMiddleware.run(rootSaga);

  export default store;
```


### Implementando o arquivo Home.js
src/pages/Home.js
```js
  . . . 
  handleAddProduct = id => {
    const { addToCartRequest } = this.props;
    addToCartRequest(id);
  };
  . . . 
```
