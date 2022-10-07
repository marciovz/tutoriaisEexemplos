# ESLINT - Typescript

[ESLint](https://eslint.org/)

## Instalação

Instalar a biblioteca do eslint como dependência de desenvolvimento.

```cmd
$ npm install eslint -D
```

Retirar a configuração do eslint nas propriedades do package.json, caso exista.


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
      - yes
    Where does your code run?
      - Browser
    How would you like to define a style for your project?
      - Use a popular style guide
    Which style guide do you want to follow?
      - Airbnb
    What format do you want your config file to be in?
      - Json
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
      'plugin:react/recommended',
      'plugin:@typescript-eslint/recommended',
    ],
    globals: {
      Atomics: 'readonly',
      SharedArrayBuffer: 'readonly',
    },
    parser: '@typescript-eslint/parser',
    parserOptions: {
      ecmaFeatures: {
        jsx: true,
      },
      ecmaVersion: 2018,
      sourceType: 'module',
    },
    plugins: [
      'react',
      "react-hooks",
      "@typescript-eslint"
    ],
    "rules": {
      "react-hooks/rules-of-hooks": "error",
      "react-hooks/exhaustive-deps": "warn",
      "react/jsx-filename-extension": [1, { "extensions": [".tsx"] }],
      "import/prefer-default-export": "off",
      "import/extensions": [
        "error",
	      "ignorePackages",
	      {
	        "ts": "never",
	        "tsx": "never"
	      }
      ]
    },
    "settings": {
       "import/resolver": {
          "typescript": {}
       }
    }
  }
```

Instalar a biblioteca eslint-import-resolver-typescript como dependência de desenvolvimento.
```cmd
$ npm install eslint-import-resolver-typescript -D
```

Adicionar os seguintes arquivos no .eslintignore:

.eslintignore
```
  node_modules
  build
  src/react-app-env.ts
  **/*.js
```
