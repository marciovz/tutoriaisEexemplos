# EVENTOS

### Adicionando apenas um evento

```html
<div>
  <button>Clique aqui</button>
</div>
```

```js
const elemento_botao = document.querySelector("button");
elemento_botao.onclick = function () {
  console.log("clicou...");
};
```

### Adicionando um ou mais eventos (addEventListener)

```html
<div>
  <button>Clique aqui</button>
</div>
```

```js
const elemento_botao = document.querySelector("button");
elemento_botao.addEventListener("click", function () {
  console.log("Clicou no botão");
});

elemento_botao.addEventListener("mouseover", function () {
  console.log("mouse over");
});
```
