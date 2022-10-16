# Estrutura do zero com Babel e Webpack

### Iniciar uma pasta para o projeto

```cmd
$ mkdir projeto
$ cd projeto
$ npm init -y

$ code .
```

### Instalar as bibliotecas do babel e webpack como dependências de desenvolvimento

```cmd
  $ npm install @babel/core @babel/preset-env @babel/preset-react babel-loader -D

  $ npm install webpack webpack-cli webpack-dev-server -D

  $ npm install style-loader css-loader file-loader -D

  $ npm install react react-dom
```

### Criar o arquivo de configuração do babel
babel.config.js
```js
  module.exports = {
    presets: [
      "@babel/preset-env",
      "@babel/preset-react"
    ],
  }
```

### Criar o arquivo de configuração do webpack
webpack.config.js
```js
  const path = require('path');

  module.exports = {
    entry: path.resolve(__dirname, 'src', 'index.js'),
    output: {
      path: path.resolve(__dirname, 'public'),
      filename: 'bundle.js'
    },
    module: {
   	  rules: [
        {
          test: /\.js$/,
       	  exclude: /node_modules/,
       	  use: {
         	  loader: 'babel-loader'
       	  }
        },
        {
          test: /\.css$/,
          use: [
            { loader: 'style-loader' },
            { loader: 'css-loader' },
          ]
        },
        {
          test: /.*\.(gif|png|jpe?g)$/i,
          use: {
            loader: 'file-loader'
          }
        }
      ]
 	  },
    devServer: {
      contentBase: path.resolve(__dirname, 'public'),
    }
  };
```

### Adicionar o script no arquivo package.json
package.json
```json
  . . . 

  "scripts": {
    "build": "webpack --mode production",
    "dev": "webpack-dev-server --mode development"
  }
  . . . 
```

### Criar os arquivos de entrada da aplicação
public/index.html
```html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>ReactJS</title>
    </head>
    <body>
      <div id="app"></div>
      <script src="./bundle.js"></script>
    </body>
  </html>
```

src/index.js
```js
 	import React from 'react';
	import { render } from 'react-dom';
	
	import App from './ App';
	
	render(<App />, document.getElementById('app')); 
```

src/App.js
```js
	import React from 'react';
	
	function App() {
	 	return <h1>Projeto com Bable e Webpack</h1>
	}
	
	export default App;
```

 