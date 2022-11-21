# Pegando um elemento html no documento.

### GetElementById

Retorna o elemento com o id selecionado.

```html
<body>
  <h1>Titulo</h1>
  <p id="paragrafo">Isso é um paragrafo</p>
</body>
```

```js
const elemento = document.getElementById("paragrafo");
console.log(elemento);
```

### GetElementsByClassName

Retorna uma HTMLCollections com os elementos com a classe selecionada.

```html
<body>
  <ul>
    <li class="lista">item um</li>
    <li class="lista">item dois</li>
    <li class="lista">item tres</li>
  </ul>
</body>
```

```js
const elemento = document.getElementsByClassName("lista");
console.log(elemento);
```

### GetElementsByTagName

Retorna uma HTMLCollections selecionadas pela tag.

```html
<body>
  <ul>
    <li>item um</li>
    <li>item dois</li>
    <li>item tres</li>
  </ul>
</body>
```

```js
const elemento = document.getElementsByTagName("li");
console.log(elemento);
```

### QuerySelector

Retorna um elemento selecionado por um seletor.

```html
<body>
  <ul>
    <li class="active">item um</li>
    <li>item dois</li>
    <li>item tres</li>
  </ul>
</body>
```

```js
const elemento = document.querySelector("ul li.active");
console.log(elemento);
```

### QuerySelectorAll

Retorna uma NodeList selecionado por um seletor.

```html
<body>
  <ul>
    <li class="active">item um</li>
    <li>item dois</li>
    <li>item tres</li>
  </ul>
</body>
```

```js
const elemento = document.querySelectorAll("ul li");
console.log(elemento);
```
