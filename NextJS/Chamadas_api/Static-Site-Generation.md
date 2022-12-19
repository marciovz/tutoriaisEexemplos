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

## Estratégias para geração estática

As páginas estáticas pode ser todas geradas antes da página ser renderizada, porém se o número de páginas forem muito grande, 1000 por exemplo, isso irá refletir em uma demora para renderização da página inicial.
Para resolver isso, temos 3 estratégia de geração de páginas estática.

- Gerar as páginas estáticas durante a build;
- Gerar a página estática no primeiro acesso;
- Gerar as principais páginas durante a build, e as demais durante o primeiro acesso;

### Gerando todas as páginas estáticas durante o primeiro acesso

Para gerar as páginas estáticas durante o primeiro acesso, basta passar as configurações vazia no paths do metodo getStaticpaths.

```js
export const getStaticPaths: GetStaticPaths = () => {
  return {
    paths: [],
    fallback: "blocking",
  };
};
```

### Gerando todas as páginas estáticas durante a build

Gerar as páginas estáticas durante a build, basta passar todas slugs no parametros das paths.

```js
export const getStaticPaths: GetStaticPaths = () => {
  return {
    paths: [
      { params: { slug: "slug-page-01" } },
      { params: { slug: "slug-page-02" } },
      { params: { slug: "slug-page-03" } },
      { params: { slug: "slug-page-04" } },
      { params: { slug: "slug-page-05" } },
    ],
    fallback: "blocking",
  };
};
```

### Gerando algumas páginas durante a build e as demais no primeiro acesso

Nesse basta passar apenas as principais slugs para serem geradas estaticamente, e as demais serão geradas no primeiro acesso.

```js
export const getStaticPaths: GetStaticPaths = () => {
  return {
    paths: [
      { params: { slug: "slug-page-01" } },
      { params: { slug: "slug-page-02" } },
    ],
    fallback: "blocking",
  };
};
```

## Configurando o parametro fallback

### fallback = true

Se a página estática não for encontrada, ela vai ser carregada pelo lado do cliente,
carregado primeiro a página e depois os dados.

### fallback = false

Se a página estática não for encontrada, será retornado um 404 de página não encontrada.

### fallback = blocking

Se a página estática não for encontrada, ela será carregada pelo lado do servidor, e só renderizar no cliente quando toda a página estiver carregada.
