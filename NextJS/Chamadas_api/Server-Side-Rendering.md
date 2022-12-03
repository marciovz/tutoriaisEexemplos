# SERVER SIDE RENDERING (SSR)

É o processo de renderização pelo lado do servidor. Toda o processo de rederização e busca de dados nas api são feitas pelo servidor, e somente depois da página estar pronta ela é enviada ao cliente.

Utiliza-se a função GETSERVERSIDEPROPS do Nextjs para fazer uso do SSR.

No exemplo abaixo, o servidor do nextjs primeiro faz uma requisição a um servidor qualquer buscado os dados do usuário.
Ao receber os dados do usuário, o servidor do nextjs constrói a página já com os dados e envia para o cliente.
Assim o cliente não precisa buscar os dados do usuário na primeira renderização.

```tsx
import { GetServerSideProps } from "next";

interface HomeProps {
  user: {
    id: string;
    name: string;
    email: string;
  };
}

export default function Home({ user }: HomeProps) {
  return (
    <>
      <p>{user.id}</p>
      <p>{user.name}</p>
      <p>{user.email}</p>
    </>
  );
}

export const getServerSideProps: GetServerSideProps = async () => {
  const user = await axios.get("user");

  return {
    props: {
      user,
    },
  };
};
```
