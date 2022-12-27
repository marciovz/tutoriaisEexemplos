# PREFETCH DE DADOS COM REACT QUERY

O prefetch de dados é a antecipação da busca dos dados antes de elas serem necessárias, armazenando-as em cach.

Exemplo, fazer a requisição dos dados ao passar o mouse por cima do link de um item em uma lista de usuários por exemplo.

src/pages/users/index.tsx

```tsx
. . .
async function handlePrefectchUser(userid: number) {
  await queryClient.prefetchQuery(['user', userId], async () => {
    const response = await api.get(`users/${userId}`);
    return response.data;
  },{
    staleTime: 1000 * 60 * 10 // 10 minutos
  })
}
. . .
<Box>
  <Link color="purple.400" onMouseEnter={() => handlePrefectUser(Number(user.id))}>
    <Text fontWeight="bold>{user.name}</Text>
  </Link>
</Box>
```
