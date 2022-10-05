# Iniciando um Projeto Reactjs com Vite

## Site oficial

[vitejs.dev](https://vitejs.dev/)

## Iniciando o projeto

Rodar o comando create vite para criar um projeto com Vite.
```cmd
$ npm create vite@latest
$ project name: nome_do_projeto
$ template: react
$ variantes: react-ts
```

Instalar as dependências do projeto.
 ```cmd
$ npm install  
 ```

Rodar o projeto.
```cmd
$ npm run dev
```

## Configurando uma porta padrão

vite.config.js
```ts
  import { defineConfig } from 'vite'
  import react from '@vitejs/plugin-react'

  export default defineConfig({
    plugins: [react()],
    server: {
      port: 3001,
    }
  })
```