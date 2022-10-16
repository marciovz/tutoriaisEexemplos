# REDUX SAGA

### instalar as seguintes bibliotecas

```cmd 
$ npm install redux redux-saga react-redux immer
```

### Criar o arquivo de auth/reducer
src/store/modules/auth/reducer.js
```js
	const INITIAL_STATE = {};
	
	export default function auth(state = INITIAL_STATE, action) {
  		switch (action.type) {
    			default:
      				return state;
  		}
	}
```

### Criar o arquivo auth/sagas.js
src/store/modules/auth/sagas.js
```js
	import { all } from 'redux-saga/effects';
	
	export default all([]);
```

### Criar o arquivo rootReducer.js
src/store/modules/rootReducer.js
```js
	import { combineReducers } from 'redux';
	
	import auth from './auth/reducer';
	
	export default combineReducers({
  		auth,
	});
```

### Criar o arquivo rootSaga.js
src/store/modules/rootSaga.js
```js
	import { all } from 'redux-saga/effects';
	
	import auth from './auth/sagas';
	
	export default function* rootSaga() {
  		return yield all([auth]);
	}
```

### Criar o arquivo createStore.js
src/store/createStore.js
```js
	import { createStore, compose, applyMiddleware } from 'redux';
	
	export default (reducers, middlewares) => {
  		const enhancer =
    			process.env.NODE_ENV === 'development'
      				? compose(console.tron.createEnhancer(), applyMiddleware(...middlewares))
      				: applyMiddleware(...middlewares);

	  	return createStore(reducers, enhancer);
	};
```

### Criar o arquivo store/index.js
src/store/index.js
```js
	import createStore from './createStore';
	
	import rootReducer from './modules/rootReducer';
		
	const store = createStore(rootReducer);
		
	export default store;
```

### No arquivo App.js
src/App.js
```js
	import React from 'react';
	import { Provider } from 'react-redux';
	import { Router } from 'react-router-dom';
	
	import Routes from '~/routes';
	import history from '~/services/history';
	
	import store from './store';

	import GlobalStyle from './styles/global';
	
	function App() {
  		return (
    			<Provider store={store}>
      				<Router history={history}>
        				<Routes />
        				<GlobalStyle />
      				</Router>
    			</Provider>
  		);
	}

	export default App;
```