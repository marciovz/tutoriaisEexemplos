# ESLINT - Javascript

[ESLint](https://eslint.org/)

## Instalação

Instalar a biblioteca do eslint como dependência de desenvolvimento.

```cmd
$ npm install eslint -D
```


Iniciar a configuração do eslint;
```cmd
$ npm eslint --init
    How would you like to use ESLint?
      - To check syntax, ding problems, and enforce style
    What type of modules does your project use?
      - Javascript modules (import/export)
    Which framework does your project use?
      - React
    Does you project use TypeScript?
      - no
    Where does your code run?
      - Browser
    How would you like to define a style for your project?
      - Use a popular style guide
    Which style guide do you want to follow?
      - Airbnb
    What format do you want your config file to be in?
      - Javascript
    Would you like to install them now with npm?
      - yes
```

Será gerado um arquivo .eslintrc.js automaticamente na raiz do projeto.

.eslintrc.js
```js
  module.exports = {
    env: {
      brower: true,
      es6: true,
    },
    extends: [
      'airbnb',
    ],
    globals: {
      Atomics: 'readonly',
      SharedArrayBuffer: 'readonly',
    },
    parser: 'babel-eslint',
    parserOptions: {
      ecmaFeatures: {
        jsx: true,
      },
      ecmaVersion: 2018,
      sourceType: 'module',
    },
    plugins: [
      'react',
    ],
    rules: {
      'react/jsx-filename-extension': [
        'warn',
        { extensions: ['.jsx', 'js'] }
      ],
      'import/prefer-default-export': 'off'
    },
  }
```