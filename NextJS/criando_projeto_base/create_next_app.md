# INICIANDO PROJETO NEXTJS

Documentação do nextjs

[Documentação Nextjs](https://nextjs.org/docs)

### Criando projeto base com create next-app

```cmd
npx create-next-app@latest nome_projeto
```

### Configurando a estrutura de pastas e arquivos do projeto

Podemos excluir:

- a pasta styles;
- o arquivo readme.md;
- o arquivo public/favicom.ico;
- o o arquivo public/versel.svg;
- o arquivo Pages/api.js

Editar o arquivo index.js da pasta Pages.

```js
export default function Home() {
  return <h1>Hello World!</h1>;
}
```

Retirar a importação do ícone favicom no arquivo \_app.js da pasta pages.

```js
function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
export default MyApp;
```

Criar uma pasta src na raiz do projeto e mover a pasta Pages para dentro de src.

obs.: A pasta Pages deve obrigatóriamente estar na raíz do projeto ou dentro da pasta src.

### Rodando o projeto

```cmd
npm run dev
```

## Adicionando o Typescript no projeto nextjs com javascript.

Obs.: Podemos criar a extrutura base do projeto nextjs já com typescript configurado utilizando a flag --typescript na criação do projeto.

### Instalando as bibliotecas

```cmd
npm install typescript -D
npm install @types/react -D
npm install @types/node -D
```

### Alterando as extensões dos arquivos

alterar as extensões dos arquivos .jsx para .tsx;

Rodar o projeto para criar o arquivo de configuração do typescript (tsconfig.json), e o arquivo de tipagens do next (next-env.d.ts)

```cmd
npm run dev
```

Adicionar a declaração dos tipos das propriedades do component App

```js
import { AppProps } from "next/app";

function MyApp({ Component, pageProps }: AppProps) {
  return <Component {...pageProps} />;
}
export default MyApp;
```
