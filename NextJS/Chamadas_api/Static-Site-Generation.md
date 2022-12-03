# STATIC SITE GENERATION (SSG)

O SSG é um processo semelhante ao SSR. Ele também entrega ao cliente uma página com todos os dados preenchidos.
A diferença é que o SSG possuí um mecânismo que permite gerar página estáticas armazenadas em cash e fornecelás quando outras requisições aos mesmos dados forem feitas.

```tsx
import { GetStaticProps } from "next";

interface HomeProps {
  post: {
    id: string;
    title: string;
    description: string;
  };
}

export default function Home({ user }: HomeProps) {
  return (
    <>
      <p>{post.id}</p>
      <p>{post.title}</p>
      <p>{post.description}</p>
    </>
  );
}

export const getStaticProps: GetStaticProps = async () => {
  const post = await axios.get("post");

  return {
    props: {
      post,
    },
    revalidate: 60 * 60 * 24, // 24 hours
  };
};
```
