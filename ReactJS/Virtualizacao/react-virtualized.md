# VIRTUALIZACAO COM REACT-VIRTUALIZE

A virtualização que seja renderizado em tela apenas os itens que estão visíveis no navegador do ususário,
evitando que seja rederizado itens que não aparecem em tela.

Pode ser usado para:

- listas
- grids
- tabelas
- masonry layout
- colections

## Instalando a biblioteca React-Virtualized

```cmd
npm install react-virtualized
npm install @types/react-virtualized -D
```

## Codigo Exemplo

No exemplo abaixo, o react virtualize irá renderizar apenas a quantidade configurada no elemento List.

src/components/SerachResults.tsx

```tsx
import { List, ListRowRenderer } from "react-virtualized";

import { ProductItem } from "./ProductItem";

interface SerchResultsProps {
  totalPrice: number;
  results: Array<{
    id: number;
    price: number;
    priceFormatted: string;
    title: string;
  }>;
  onAddToWishList: (id: number) => void;
}

export function SearchResults({
  totalPrice,
  results,
  onAddToWishList,
}: SearchResultsProps) {
  const rowRenderer: ListRowRenderer = ({ index, key, style }) => {
    return (
      <div key={key} style={style}>
        <ProductItem
          product={results[index]}
          onAddToWishList={onAddToWishList}
        />
      </div>
    );
  };

  return (
    <div>
      <h2>{totalPrice}</h2>

      <LIst
        height={300}
        rowHeight={30}
        width={900}
        overscanRowCount={5}
        rowCount={results.length}
        rowRenderer={rowRenderer}
      />
    </div>
  );
}
```
