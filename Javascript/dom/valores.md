## ALTERANDO VALORES

### Atribuindo um valor a um elemento (value)

```html
<div>
  <input />
</div>
```

Atribuindo um valor a um elemento

```js
const elemento = document.querySelector("input");
elemento.value = "Digite seu nome.";
```

### Buscando um valor em um elemento (value)

```html
<div>
  <input value="digite algo aqui..." />
</div>
```

Atribuindo um valor a um elemento

```js
const elemento = document.querySelector("input");
let valor = elemento.value;
console.log(valor);
```
