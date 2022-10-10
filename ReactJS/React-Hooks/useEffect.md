# useEFFECT

O hook useEfect permite a execução de algum código, como uma requisição de dados a uma API, 
toda vez que o componente é criado na tela ou quando uma determinada variavel tiver seu valor alterado.


```js
  const [filter, setFilter] = useState('')

  useEffect(() => {
    fetch(`http://filmes.com/?query${filter}`)
  }, [filter])
```

Toda vez que o estado filter é modificado, o useEffect dispara uma nova requisição 
passando o novo valor do filtro.

