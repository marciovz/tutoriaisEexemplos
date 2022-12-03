# API ROUTES NO NEXTJS

Podemos implementar rotas api que rodam no servidor next, evitando que dados e endereços da aplicação fique exposto no frontend da aplicação.

Para implementar uma rota api no nextjs, basta implementar a api desejada dentro da pasta pages/api, que o nextjs automaticamente implementará a api no servidor nextjs.

O nome do serviço será o nome do arquivo implementado dentro da pasta pages/api.

pages/api/users.ts

```tsx
import { NextApiRequest, NextApiResponse } from 'next';

export default ( request: NextApiRequest, response: NextApiResponse) => {
  const users = [
    {
      id: 1,
      name: 'John Due'
      email: 'john.due@email.com'
    },
    {
      id: 2,
      name: 'Mary Due'
      email: 'mary.due@email.com'
    },
  ]

  return response.json(users);
}
```

Para acessa o serviço basta acessar o endereço da aplicação na rota api/nome_serviço

```
EX.: http://localhost:3000/api/users

```