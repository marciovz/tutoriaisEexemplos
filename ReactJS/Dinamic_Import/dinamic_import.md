# DINAMIC IMPORTS (CODE SPLITTING)

É uma técnica utilizada para fazer a importações de arquivos (modulos, funções ou outros arquivos) somente no momento em que eles forem utilizados.

Para trabalhar com dinamic import podemos trabalhar tanto com a função lazy do react ou se estivermos trabalhando com nextjs, podemos utilizar a função dynamic do 'next/dynamic' para poder trabalhar com server side rendering SSR;

## Exemplo de uso

### AddProductToWishList

src/components/AddProductToWishList.tsx

```tsx
export interface AddProductToWishListProps {
  onAddToWishList: () => void;
  onRequestClose: () => void;
}

export function AddProductToWishList({
  onAddToWishList,
  onRequestClose,
}: AddProductToWishListProps) {
  return (
    <span>
      Deseja adicionar aos favoritos:
      <button onClick={onAddToWishList}>Sim</button>
      <button onClick={onRequestClose}>Não</button>
    </span>
  );
}
```

### ProductItem

src/components/ProductItem.tsx

```js
import { memo, useState, lazy } from 'react';
import { AddProductToWishListProps } from './AddProductToWishList';
import dynamic from 'next/dynamic';
// import { AddProductToWishList } from './AddProductToWishList';

const AddProductToWishList = dynamic<AddProductToWishListProps>(() => {
  // return import('./AddProductToWishList') // Se o module estiver com export default
  return import('./AddProductToWishList').then(mod => mod.AddProductToWishList)
}, {
  loading: () => <span>carregando...</span>
})

interface ProductItemProps {
  product: {
    id: number;
    price: number;
    price:Formatted: string;
    title: string;
  }
  onAddToWishList: (id:number) => void;
}

export function ProductItemcomponent({ product, onAddToWishList}: ProductItemProps) {
  const [ isAddingToWishList, setIsAddingToWishList ] = useState(false);

  return (
    <div>
      {product.title} - <strong>{product.priceFormatted</strong>
      <button onClick={() => setIsAddingToWishList(true)}>Adicionar aos favoritos</button>

      { isAddingToWishList && (
        <AddproductToWishList
          onAddToWishList={() => onAddToWishList(product.id)}
          onRequestClose={() => setIsAddingToWishList(false)}
        />
      )}
    </div>
  )
}

```
