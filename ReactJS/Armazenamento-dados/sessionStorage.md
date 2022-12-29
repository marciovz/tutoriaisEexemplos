# ARMAZENAMENTO DE DADOS NA SESSION

A sessionStorage não fica disponível para outras sessões, ou seja, se o navegador for fechado, os dados no sessionStorage será perdido.
Portanto ele é indicado para armazenamento de dados que possam ser recuperados de outros locais quando o navegador for iniciado.
Está apenas disponível no browser do frontend, e não pode ser acessado no backend do Nextjs por exemplo.

## Alterar os métodos abaixo.

### Armazenando dado no localstorage

```js
const user = {
  name: "Manoel Vieira",
  email: "manoel.vieira@email.com",
};

localstorage.setItem("user", JSON.stringify(user));
```

### Buscando dados no localstotage

Os dados vem no formato string. Para casos de objetos, devemos converter-los novamente para o formato inicial.

```js
const dataUser = localstorate.getItem("user");
const user = JSON.parser(dataUser);
```

### Apagando dados do localstorage

```js
localstorage.removeItem("user");
```
