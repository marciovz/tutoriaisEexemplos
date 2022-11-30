# UTILIZANDO FONTES EXTERNAS

As fontes externas devem ser adicionadas na tag head do arquivo index.html;
No nextjs esse arquivo é adicionado automaticamente, e para adicionar configurações nesse arquivo devemo sobrescrever esse arquivo.

### Configurando a fontes externas no arquivo \_document.tsx

o arquivo \_document.tsx deve ficar dentro da pasta pages e ele é lido uma única vez na inicialização do projeto.
Para adicionar-mos as fontes ou outra configurações necessárias devemos sobrescrever esse arquivo da seguinte forma:

```tsx
import Document, { Html, Head, Main, NextScript } from 'next/document';

export default class myDocument extends Document {
  render() {
    return (
      <Html>
        <Head>
          <link rel='preconnect' href='https://fonts.googleapis.com' />
          <link rel='preconnect' href='https://fonts.gstatic.com' />
          <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&family=Roboto:wght@400;700;900&display=swap" rel="stylesheet" />
        </Head>
        <body>
          <Main />
          <NextScript />
        <body>
      </Html>
    )
  }
}
```
