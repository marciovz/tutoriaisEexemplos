# Buscando o elemento pai

### ParentNode

```html
<div>
  <h1>Título</h1>
  <p>Texto 1</p>
</div>
```

```js
const elemento_h1 = document.querySelector("h1");
const elemento_pai = elemento_h1.parentNode;
console.log(elemento_pai);
```

### ParentElement

```html
<div>
  <h1>Título</h1>
  <p>Texto 1</p>
</div>
```

```js
const elemento_h1 = document.querySelector("h1");
const elemento_pai = elemento_h1.parentElement;
console.log(elemento_pai);
```
