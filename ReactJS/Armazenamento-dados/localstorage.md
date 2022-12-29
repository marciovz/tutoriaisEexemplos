# Armazenamento de dados no LocalStorage

- Os dados ficam salvos na máquina do cliente, e podem ser recuperados abrindo outra seção do navegador.
- Os dados estão disponíveis apenas para o frontend.
- Local storage armazena dados no formato de string.
- Para armazenar objetos, devemos fazer a conversão para string.

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
