# useMemo

Evita que um determinado cálculo seja refeito em diversas renderizações onde suas dependências não tenham sido alteradas.

Usado também para resolver problemas de igualdade referencial, quando os componentes utilizam o memo().

Não é recomendado para uso em cálculos simples, pois o fato so useMemo ter que fazer comparações dos estados,
o esforço gasto não justifique o seu uso.


```js
  const [movies, setMovies] = useState([])
  
  const moviesListSize = useMemo(() => {
    return movies.lenght
  }, [movies])

```

Dessa forma o calculo é realizado apenas quando o estado movies for alterado, evitando 
cálculos desnecessários a cada renderização.
