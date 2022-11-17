# ALTERANDO CONTEUDO

## TextContent

### Atribuindo um conteudo de texto no elemento html

```html
<div>
  <p>texto 1</p>
</div>
```

```js
const elemento = document.querySelector("p");
elemento.textContent = "texto 2";
```

### Buscando um conteudo de texto (TextContent) no elemento html

```html
<div>
  <p>texto 1</p>
</div>
```

```js
const elemento = document.querySelector("p");
let conteudo = elemento.textContent;
console.log(conteudo);
```

## InnerText

### Atribuindo um conteudo de texto no elemento html

```html
<div>
  <!--adiciona aqui-->
</div>
```

```js
const elemento = document.querySelector("p");
elemento.innerText = "texto 2";
```

### Buscando um conteudo de texto no elemento html

```html
<div>
  <p>texto 1</p>
</div>
```

```js
const elemento = document.querySelector("p");
let conteudo = elemento.innerText;
console.log(conteudo);
```

## InnerHTML

### Atribuindo um elemento html dentro de outro elemento html

```html
<div></div>
```

```js
const elemento = document.querySelector("div");
elemento.innerHTML = "<h1>Titulo</h1>";
```
