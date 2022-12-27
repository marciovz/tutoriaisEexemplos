# CRIANDO NOVOS DADOS COM MUTATIONS

As mutations é um método do React Query que auxilia na criação de novos dados, e invalidação dos dados armazenados em cache.

## Adicionando um novo dado

No exemplo abaixo, a função createUser adiciona um novo usuário e invalida os dados do cache.

```ts
import { useMutatiion } from 'react-query';
. . .

const createUser = useMutation(async (user: CreateUserFormData) => {
  const response = await api.post('users', {
    user: {
      ...user,
      create_at: new Date(),
    }
  })
  response.data.user;
},{
  onSuccess: () => {
    queryClient.invalidateQueries('users');
  }
});
. . .

const handleCreateUser: SubmitHandler<CreateUserformData> = async (values) => {
  await createUser.mutateAsync(values)
  router.push('/users');
}
```
