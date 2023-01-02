# useCallback

Utilizado para evitar reescrita de funções toda vez que houver uma renderização da página.
Se a função for uma função simples, não é necessário utilizar useCallback por que ela precisa fazer comparações de estados, que para funções mais simples esses esforços se equiparam.

Mais indicado para :

- funções que estão sendo repassadas para outros componentes;
- funções de um contexto onde mais de um componente tem acesso a essa função;

```js
const [movie, setMovie] = useState(null);

const formatPrice = useCallback(() => {
  return Intl.NumberFormat("pt-br", {
    style: "currency",
    currency: "BRL",
  }).format(movie.price);
}, [movie]);
```

Referência

[Rocketseat - youtube](https://www.youtube.com/watch?v=NmU2nNehNNY)

### Exemplo de uso

Exemplo 2

```js
import { useCallback } from "react";
import { ProductItem } from "./ProductItem";

export function SearchResults({ results }) {
  const addToWishList = useCallback(async (id) => {
    await api.post("api/productListWish", {
      productId: id,
    });
  }, []);

  return (
    <div>
      <h2>{totalPrice}</h2>

      <Component addToWishList={addToWishList} />

      {results.map((product) => {
        return <Productitem product={product} />;
      })}
    </div>
  );
}
```
