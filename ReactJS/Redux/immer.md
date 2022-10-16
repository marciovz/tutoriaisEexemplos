# Alterando Objetos Imutáveis com IMMER

### Instalar a biblioteca do immer
```cmd
$ npm install immer
```

### Manipulando objetos imutáveis
Importar a função produce do immer e manipular os objetos como rascunhos

reducer.js
```js
    import produce from 'immer';

    export default function cart(state = [], action) {
      switch (action.type) {
        case 'ADD_TO_CART':
          return produce(state, draft => {
            const productIndex = draft.findIndex(p => p.id === action.product.id);
            if (productIndex >= 0) {
              draft[productIndex].amount += 1;
            } else {
              draft.push({
                ...action.product,
                amount: 1,
              });
            }
          });
        default:
          return state;
  			}
		}

```