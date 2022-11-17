# MANIPULANDO CLASSES

- elemento.classlist.add('ativo')
- elemento.classlist.remove('ativo')
- elemento.classlist.toogle('ativo')

### ADD

Adiciona uma class em um elemento html

```html
<div>
  <span>Titulo</span>
</div>
```

```js
const elemento = document.querySelector("span");
elemento.classList.add("selecionado");
```

### REMOVE

Remove uma class de um elemento html

```html
<div>
  <span class="selecionado">Titulo</span>
</div>
```

```js
const elemento = document.querySelector("span");
elemento.classList.remove("selecionado");
```

### TOGGLE

Se a classe existir, remove uma class de um elemento html, senão adiciona.

```html
<div>
  <span class="selecionado">Titulo</span>
</div>
```

```js
const elemento = document.querySelector("span");
elemento.classList.toggle("selecionado");
```
