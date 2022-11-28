# MIRAGEJS

O miragejs é um servidor api que quando instalado roda junto a aplicação interceptando as requisições lançadas e responsendo-as de forma a auxiliar no desenvolvimento de frontends sem a necessidade de ter um backend rodando.

[MIRAGEJS]('https://miragejs.com)

### Instalando a biblioteca do miragejs

```cmd
$ npm install miragejs -D
```

### Configurando o Miragejs

Definindo as rotas da api

```js
import { createServer, Model } from "miragejs";
import { App } from "./App";

createServer({
  models: {
    users: Model,
  },

  seeds(server) {
    server.db.loadData({
      users: [
        {
          id: 1,
          name: "John Due",
          email: "john.due@email.com",
          createdAt: new Date(),
        },
        {
          id: 2,
          name: "Marie Due",
          email: "marie.due@email.com",
          createdAt: new Date(),
        },
      ],
    });
  },

  routes() {
    this.namespace = "api";

    this.get("/users", () => {
      return this.schema.all("user");
    });

    this.post("/users", (schema, request) => {
      const data = JSON.parse(request.requestBody);
      return schema.create("user", data);
    });
  },
});

ReactDom.render(
  <React.StrictMode>
    <app />
  </React.StrictMode>,
  document.getElementById("root")
);
```

### Configurando a API

```js
import axios from "axios";

export const api = axios.create({
  baseURL: "hppt://localhost:3000/api",
});
```

### Chamando a API

```js
import { useEffect } from "react";
import { api } from "./../services/api";

export function Users() {
  useEffect(() => {
    api.get("users").then((response) => console.log(response.data));
  }, []);

  return (
    <div>
      <p>users</p>
    </div>
  );
}
```
