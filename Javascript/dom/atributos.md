# MANIPULANDO ATRIBUTOS

- setAttribute("attribute", "value")
- getAttribute("attribute")
- removeAttribute("attribute")

### SetAttribute

```html
<div>
  <a>Clique aqui</a>
</div>
```

```js
const elemento = document.querySelector("a");
elemento.setAttribute("active", true);
```

### GetAttribute

```html
<div>
  <a active="true">Clique aqui</a>
</div>
```

```js
const elemento = document.querySelector("a");
const attrActive = elemento.getAttribute("active");
console.log(attrActive);
```

### RemoveAttribute

```html
<div>
  <a active="true">Clique aqui</a>
</div>
```

```js
const elemento = document.querySelector("a");
elemento.removeAttribute("active");
```
