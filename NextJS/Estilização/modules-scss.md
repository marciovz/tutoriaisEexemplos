# ESTILIZAÇÃO CSS Modules e SASS

O CSS Module é uma ferramenta de estilização css que criar escopos de estilização em elementos (SCOPE CSS).

No Nextjs, todo arquivo terminado com .module.css, ele será um arquivo de estilo css tipo SCOPED, ou seja, ele será aplicado a um escopo de componente.

As estilizações dos modules CSS precisam obrigatóriamente iniciar com uma classe.

O SASS é uma ferramenta de estilização que permite utilizar funcionalidades de estilização em cascata, variáveis e outras funcionalidades, e na hora de rodar ela complila para css comum toda essas funcionalidades, permitindo uma flexibilidade na hora de estilizar os componentes.

### Instalando a biblioteca do SASS

obs.: existem dois tipos de sintaxe de estilização sass:

- .sass - que usa o escopo por identação sem chaves
- .scss - que usa o escopo delimitado por chaves

Utilizaremos o SCSS.

```cmd
npm install sass
```

### Extensão CSS Modules para VSCode.

Podemos instalar a extensão CSS Modules (Visual Studio Code extension for CSS Modules) do fornecedor clinyoung.

### Criando o arquivo home (index.tsx)

src/pages/index.tsx

```tsx
import styles from "../styles/home.module.scss";

export default function Home() {
  return (
    <h1 className={styles.title}>
      Hello World!<span>com SASS</span>
    </h1>
  );
}
```

### Criando um arquivo de estilo CSS Module e SASS

src/styles/home.module.scss

```css
.title {
  color: red;

  span {
    color: blue;
  }
}
```

#
