# Armazenando Dados no Storage com Redux-Persist

### Instalar a biblioteca redux-presist
```cmd
$ npm install redux-persist
```

### Implementando o arquivo persitReducer.js
src/store/persistReducer.js
```js
  import storage from 'redux-persist/lib/storage';
  import { persistReducer } from 'redux-persist';

  export default reducers => {
    const persistedReducer = persistReducer(
      {
        key: 'gobarber',
        storage,
        whitelist: ['auth', 'user'],
      },
      reducers
    );
    return persistedReducer;
  };
```

### Implementando o arquivo index.js
src/store/index.js
```js
  import { persistStore } from 'redux-persist';
  import createSagaMiddleware from 'redux-saga';

  import createStore from './createStore';
  import persistReducers from './persistReducers';

  import rootReducer from './modules/rootReducer';
  import rootSaga from './modules/rootSaga';

  const sagaMonitor =
    process.env.NODE_ENV === 'development'
      ? console.tron.createSagaMonitor()
      : null;

  const sagaMiddleware = createSagaMiddleware({ sagaMonitor });

  const middlewares = [sagaMiddleware];

  const store = createStore(persistReducers(rootReducer), middlewares);
  const persistor = persistStore(store);

  sagaMiddleware.run(rootSaga);

  export { store, persistor };
```

### Implementando o arquivo App.js
src/App.js
```js
  import { PersitGate } from ‘redux-persist/integration/react’;
  . . . 
  import { store, persistor } from ‘./store’;

  . . .
  return (
    <Provider store={store}>
      <PersistGate persistor={persistor}>
        <Router history={history}>
          <Routes />
          <GlobalStyle />
          <ToastContainer autoClose={3000} />
        </Router>
      </PersistGate>
    </Provider>
  );
```
