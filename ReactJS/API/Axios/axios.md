# REQUISIÇÕES COM A BIBLIOTECA AXIOS

## Instalação

```cmd
npm install axios

```

## Serviço de API

src/service/api.ts

```ts
import axios from "axios";

export const api = axios.create({
  baseURL: "http://localhost:3000",
});
```

## Setando headers da aplicação

Nesse exemplo estamos buscando o token da aplicação e adicionando nos cabeçalhos das requisições.

src/service/api.ts

```ts
import axios from "axios";
import { parseCookies } from "nookies";

const cookies = parseCookies();

export const api = axios.create({
  baseURL: "http://localhost:3000",
  headers: {
    Aturhorization: `Bearer ${cookies["nextauth.token"]}`,
  },
});
```

## Interceptando requisições

O axios disponibiliza um método interceptors que permite interceptarmos requisições e respostas, antes que eles seja repassadas para frente.

```ts
import axios, { AxiosError } from "axios";
import { parseCookies } from "nookies";

const cookies = parseCookies();

export const api = axios.create({
  baseURL: "http://localhost:3000",
  headers: {
    Aturhorization: `Bearer ${cookies["nextauth.token"]}`,
  },
});

api.interceptors.response.use(response => {
  return response;
}, (error: AxiosError) => {
  if(error.response.status === 401) {
    if (error.response.data?.code === 'token.expired') {
      // renovar o token
    } else {
      // deslogar o usuário
    }
  }
});
`
```
