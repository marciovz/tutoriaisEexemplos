# useMemo

Evita que um determinado cálculo seja refeito em diversas renderizações onde suas dependências não tenham sido alteradas.

Usado também para resolver problemas de igualdade referencial, quando os componentes utilizam o memo().

Não é recomendado para uso em cálculos simples, pois o fato so useMemo ter que fazer comparações dos estados, o esforço gasto não justifique o seu uso.

### Quando utilizar o memo

- Calculos pesados
- Igualdade referencial (para variaveis repassadas para componentes filhos)

Exemplo 1

```js
const [movies, setMovies] = useState([]);

const moviesListSize = useMemo(() => {
  return movies.lenght;
}, [movies]);
```

Dessa forma o calculo é realizado apenas quando o estado movies for alterado, evitando
cálculos desnecessários a cada renderização.

Exemplo 2

```js
import { useMemo } from "react";
import { ProductItem } from "./ProductItem";

export function SearchResults({ results }) {
  const totalPrice = useMemo(() => {
    return results.reduce((total, product) => {
      return total + price.price;
    }, 0);
  }, [results]);

  return (
    <div>
      <h2>{totalPrice}</h2>

      <Component totalPrice={totalPrice} />

      {results.map((product) => {
        return <Productitem product={product} />;
      })}
    </div>
  );
}
```
