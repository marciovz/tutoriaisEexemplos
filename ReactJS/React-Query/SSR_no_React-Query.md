# SSR NO REACT QUERY

Como a função getServerSide não possui acesso aos hook, porque os Hooks são componentes do frontend,
então podemos fazer uma requisição pelo lado do server repassando para o frontend esses dados.
O frontend ao receber esses dados poderá armazenar esses dados passando eles como parâmetros de inicializaçõ ao chamar o hook useUser.

## Código de exemplo

src/pages/users/index.tsx

```tsx
export default function UserList({ users }) {
  const { data, isLoading, isFetching, error } = useUsers(page, { initialData: users });

  . . .
}

export const getServerSideProps: GetServerSideProps = async () => {
  const { users } = await getUsers(1)
  return {
    props: {
      users
    }
  }
}
```

src/services/hooks/useUsers.ts

```tsx
export function UseUsers(page: number, options?: UseQueryOption) {
  return useQuery(["users", page], () => getUsers(page), {
    staleTime: 1000 * 60 * 10, // 10 minutos
    ...options,
  }) as UseQueryResult<GetUsersResponse, unknown>;
}
```
