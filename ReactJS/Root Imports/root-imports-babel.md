# ROOT IMPORTS - Babel

Importações relativas permite a navegação de importação com base na raiz do projeto.

### Instalação

Instalar as bibliotecas abaixo como dependências de desenvolvimento.
```cmd
$ npm install customize-cra -D
$ npm install react-app-rewired -D
$ npm install babel-plugin-roo-import -D
```

Criar um arquivo config-overrides.js na raiz do projeto com o seguinte código:
config-overrides.js
```js
  const { addBabelPlugin, override } = require('customize-cra');

  module.exports = override(
    addBabelPlugin([
      'babel-plugin-root-import',
      {
        rootPathSuffix: 'src',
      }
    ])
  )
```

Alterar as seguintes linhas no arquivo package.json .
```json
  "scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-scripts eject"
  }
```

### Configurando o ESLint para Root Imports

Instalar as seguintes bibliotecas:
```cmd
$ npm install eslint-import-resolver-babel-plugin-root-import -D
```
Adicionar o settings no final do arquivo .eslintrc.js

.eslintrc.js
```js
  settings: {
    "import/resolver": {
      "babel-plugin-root-import": {
        rootPathSuffix: "src"
      }
    }
  }

```
Criar um arquivo jsconfig.json na raiz do projeto.

jsconfig.json
```json
  {
    "compilerOptions": {
      "baseUrl": "src",
      "paths": {
        "~/*":["*"]
      }
    }
  }
```
