# PRETTIER - Javascript

[Prettier](https://prettier.io/docs/en/editors.html)

### Instalando o Prettier com ESLint configurado

Instalar as seguintes bibliotecas.
```cmd
$ npm install prettier -D
$ npm install eslint-config-prettier -D
$ npm install eslint-plugin-prettier -D 
$ npm install babel-eslint -D
```

Editar o arquivo .prettierrc

.prettierrc
```json
  {
    "singleQuote": true,
    "trailingComma": "es5"
  }
```
Adicionar as seguintes configurações do prettier no arquivo de configuração do ESLint:

.eslintrc.js
```js
	module.exports = {
    extends: [
      'prettier',
      'prettier/react'
    ],
    parser: 'babel-eslint',
    plugins: [
      'prettier',
    ],
	};
```
