# Requisições api com AXIOS

### Instalando a biblioteca

```cmd
$ npm install axios
$ npm install @types/axios -D
```

### Implementado serviço de requisições

Criar um arquivo api.ts

```tsx
import axios from "axios";

export const api = axios.create({
  baseURL: "http://localhost:3000/api",
});
```

### Utilizando uma chamada api axios com promise

```tsx
import { api } from "service/api";

api.get("users").then((response) => console.log(response.data));
```

### Utilizando uma chamada api axios com promise async await

```tsx
import { api } from "service/api";

async function getUsers() {
  return await api.get("users");
}

console.log(getUsers());
```
