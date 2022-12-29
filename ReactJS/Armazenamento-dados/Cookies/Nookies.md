# MANIPULANDO COOKIES COM A BIBLIOTECA NOOKIES

## Instalando a biblioteca Nookies

```cmd
npm install nookies
```

## Adicionando dados no cookies

```js
setCookie(ctx, "nomeApp.nomeVariavel", variavel, options);
```

- O parâmetro ctx recebe undefined quando rodando no frontend, e recebe um contexto quando for no backend.
- O segundo parâmetro é o nome da variável que será guardada no cookies. Recomenda-se usar o nome da aplicação na frente do nome da variável para não haver conflito de nomes com outras aplicação.
- O terceiro parâmetro é a própria variável;
- E o quarto parâmetro é opcional, podendo passar um objeto com algumas configurações para os cookies.

options:

- maxAge: 100, // é o tempo em segundos que o dado vai ficar salvo no navegador.
- path: '/', // quais endereços terão acesso ao cookie. '/' indica todos endereços da aplicação.

Exemplo:

```js
import { setCookie } from 'nookies';
. . .
setCookie(undefined, 'nextauth.token', token, {
  maxAge: 60 * 60 * 24 * 30,
  path: '/'
})

```

## Buscando dados na Cookies

```js
import { parceCookies } from 'nookies';
. . .
const cookies = parseCookies()

```

Ou utilizando desestruturação

```js
import { parceCookies } from 'nookies';
. . .
const { 'nextauth.token': token } = parseCookies()

```

## Apagando dados dos Cookies

```js
import { destroyCookie } from 'nookies';
. . .
destroyCookie(undefined, 'nextauth.token')

```
