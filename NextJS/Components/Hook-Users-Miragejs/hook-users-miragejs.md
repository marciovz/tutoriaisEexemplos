# CRIANDO UM HOOK DE USERS COM REACT-QUERY E MIRAGEJS

Esse componente fornece uma listagem de users utilizando o conceito de datafetching, requisição, cache e revalidação dos dados com a biblioteca do React-Query.
Também utiliza um servidor fake com o mirage para fornecer dados para a aplicação.

## Hook useUsers.ts

src/services/hooks/useUsers.ts

```ts
import { useQuery, UseQueryOptions, UseQueryResult } from "react-query";
import { api } from "../api";

type User = {
  id: string;
  name: string;
  email: string;
  createdAt: string;
};

type GetUsersResponse = {
  totalCount: number;
  users: User[];
};

export async function getUsers(page: number): Promise<GetUsersResponse> {
  const { data, headers } = await api.get("users", {
    params: {
      page,
    },
  });

  const totalCount = Number(headers["x-total-count"]);

  const users = data.users.map((user) => {
    return {
      id: user.id,
      name: user.name,
      email: user.email,
      createdAt: new Date(user.createdAt).toLocaleDateString("pt-Br", {
        day: "2-digit",
        month: "long",
        year: "numeric",
      }),
    };
  });

  return {
    users,
    totalCount,
  };
}

export function useUsers(page: number, options?: UseQueryOptions) {
  return useQuery(["users", page], () => getUsers(page), {
    staleTime: 1000 * 60 * 10, // 10 minutos
    ...options,
  }) as UseQueryResult<GetUsersResponse, unknown>;
}
```

## API Axios

src/services/axios.ts

```ts
import axios from "axios";

export const api = axios.create({
  baseURL: "http://localhost:3000/api",
});
```
