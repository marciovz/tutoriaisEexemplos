# PRETTIER - Javascript

[Prettier](https://prettier.io/docs/en/editors.html)

### Instalando o Prettier com ESLint já configurado

Instalar as seguintes bibliotecas.
```cmd
$ npm install prettier -D
$ npm install eslint-config-prettier -D
$ npm install eslint-plugin-prettier -D 
```

Editar o arquivo .prettierrc

.prettierrc ou 
prettier.config.js
```js
  module.exports = {
    singleQuote: true,
    trailingComma: "all",
    allowParens: 'avoid',
  }
```
Adicionar as seguintes configurações do prettier no arquivo de configuração do ESLint:

.eslintrc.js
```js
	module.exports = {
    extends: [
      "prettier/@typescript-eslint",
      "plugin:prettier/recommended"
    ],
    plugins: [
      'prettier',
    ],
    "rules": {
      "prettier/prettier":"error",
    }
	};
```

