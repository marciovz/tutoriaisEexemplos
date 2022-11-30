# ADICIONANDO CONFIGURAÇÕES DINÂMICAS NA TAG HEAD

Para cada página podemos adicionar tags no head para configurar aquela página, seja um title, uma description ou outra informação necessária.

Para isso basta importarmos a tag Head do next e informar as configurações necessárias dentro desta tag.

### Adicionando um title personalizado

```tsx
import styles from "../styles/home.module.scss";
import Head from "next/head";

export default function Home() {
  return (
    <>
      <Head>
        <title>titulo personalizado</title>
      </Head>

      <h1>Página Home</h1>
    </>
  );
}
```
