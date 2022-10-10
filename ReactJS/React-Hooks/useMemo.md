# useMemo

Utilizado quando é necessário utilizar cálculos complexos que dependam de um estado.

```js
  const [movies, setMovies] = useState([])
  
  const moviesListSize = useMemo(() => {
    return movies.lenght
  }, [movies])

```

Dessa forma o calculo é realizado apenas quando o estado movies for alterado, evitando 
cálculos desnecessários a cada renderização.
