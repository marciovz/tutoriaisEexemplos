# FORMATANDO PREÇOS COM INTL

```js
const precoFormated = new Intl.NumberFormat("pt-BR", {
  style: "currency",
  currency: "BRL",
}).format(preco);
```
