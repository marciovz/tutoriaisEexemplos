# CRIANDO E ADICIONANDO NOVO ELEMENTO HTML NA PÁGINA

## Criando o Elemento

### CreateElement

- Criando um elemento p, e adicionando um conteudo de texto.

```js
const novoElemento = document.createElement("p");
novoElemento.innerText = "Texto 1";
console.log(novoElemento);
```

## Adicionando o Elemento na Página

### Append

- Adicionando elemento p como último elemento dentro do elemento div raiz.

```html
<div id="root">
  <p>Texto 1</p>
  <!-- adiciona aqui -->
</div>
```

```js
const elemento_raiz = document.querySelector("#root");

const novoElemento = document.createElement("p");
novoElemento.innerText = "Texto 2";

elemento_raiz.append(novoElemento);
```

### Prepend

- Adicionando elemento p como primeiro elemento dentro do elemento div raiz.

```html
<div id="root">
  <!-- adiciona aqui -->
  <p>texto2</p>
</div>
```

```js
const elemento_raiz = document.querySelector("#root");

const novoElemento = document.createElement("p");
novoElemento.innerText = "Texto 1";

elemento_raiz.prepend(novoElemento);
```

### InsertBefore

- Adicionando o elemento p antes de um elemento selecionado.

```html
<div id="list">
  <p>texto 1</p>
  <!-- adiciona aqui -->
  <p id="p3">texto 3</p>
  <p>texto 4</p>
</div>
```

```js
const elemento_lista = document.querySelector("#list");
const elemento_p3 = document.querySelector("#p3");

const novoElemento = document.createElement("p");
novoElemento.innerText = "Texto 2";

elemento_lista.insertBefore(novoElemento, elemento_p3);
```
