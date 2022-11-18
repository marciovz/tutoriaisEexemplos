# Buscando Elementos Irmãos

### NextSibling

- Retorna o próximo elemento irmão. Considera texto como elemento.

```html
<div>
  <p id="p1">Texto 1</p>
  <p>Texto 2</p>
  <p>Texto 3</p>
</div>
```

```js
const elemento_div = document.querySelector("p#p1");
const proximo_irmao = elemento_div.nextSibling;
console.log(proximo_irmao);
```

### NextElementSibling

- Retorna o próximo elemento irmão

```html
<div>
  <p id="p1">Texto 1</p>
  <p>Texto 2</p>
  <p>Texto 3</p>
</div>
```

```js
const elemento_div = document.querySelector("p#p1");
const proximo_irmao = elemento_div.nextElementSibling;
console.log(proximo_irmao);
```

### PreviousSibling

- Retorna o elemento irmão anterior. Considera texto como elementos

```html
<div>
  <p>Texto 1</p>
  <p>Texto 2</p>
  <p id="p3">Texto 3</p>
</div>
```

```js
const elemento_div = document.querySelector("p#p3");
const irmao_anterior = elemento_div.previousSibling;
console.log(irmao_anterior);
```

### PreviousElementSibling

- Retorna o elemento irmão anterior.

```html
<div>
  <p>Texto 1</p>
  <p>Texto 2</p>
  <p id="p3">Texto 3</p>
</div>
```

```js
const elemento_div = document.querySelector("p#p3");
const irmao_anterior = elemento_div.previousElementSibling;
console.log(irmao_anterior);
```
