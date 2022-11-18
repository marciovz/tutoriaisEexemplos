# Buscando os elementos filhos

### ChildNodes

- Retorna uma nodelist. Retorna elementos de texto junto.

```html
<div>
  <h1>Título</h1>
  <p>Texto 1</p>
</div>
```

```js
const elemento_div = document.querySelector("div");
const lista_filhos = elemento_div.childNodes;
console.log(lista_filhos);
```

### Children

- Retorna um HtmlCollections. Apena os elementos.

```html
<div>
  <h1>Título</h1>
  <p>Texto 1</p>
</div>
```

```js
const elemento_div = document.querySelector("div");
const lista_filhos = elemento_div.children;
console.log(lista_filhos);
```

### FirstChild

- Retorna o primeiro elemento. Espaços são contados como texto.

```html
<div>
  <p>Texto 1</p>
  <p>Texto 2</p>
  <p>Texto 3</p>
</div>
```

```js
const elemento_div = document.querySelector("div");
const primeiro_filho = elemento_div.firstChild;
console.log(primeiro_filho);
```

### FirstElementChild

- Retorna o primeiro elemento.

```html
<div>
  <p>Texto 1</p>
  <p>Texto 2</p>
  <p>Texto 3</p>
</div>
```

```js
const elemento_div = document.querySelector("div");
const primeiro_filho = elemento_div.firstElementChild;
console.log(primeiro_filho);
```

### LastChild

- Retorna o últmo elemento. Espaços são contados como texto.

```html
<div>
  <p>Texto 1</p>
  <p>Texto 2</p>
  <p>Texto 3</p>
</div>
```

```js
const elemento_div = document.querySelector("div");
const ultimo_filho = elemento_div.lastChild;
console.log(ultimo_filho);
```

### LastElementChild

- Retorna o último elemento.

```html
<div>
  <p>Texto 1</p>
  <p>Texto 2</p>
  <p>Texto 3</p>
</div>
```

```js
const elemento_div = document.querySelector("div");
const ultimo_filho = elemento_div.lastElementChild;
console.log(ultimo_filho.textContent);
```
