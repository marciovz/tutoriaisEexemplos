# STYLED COMPONENT com TYPESCRIPT

## Instalar a biblioteca do Styled Component

```cmd
$ npm install styled-components
$ npm install @types/styled-components -D
```

## Estilização global

Criar um arquivo de estilização global

src/styles/global.ts
```ts
    import { createGlobalStyle } from 'styled-components';

    export default createGlobalStyle`
        * {
        margin: 0;
        padding: 0;
        outline: 0;
        box-sizing: border-box;
    }

    body {
        background: #312E38;
        color: #FFF;
        -webkit-font-smoothing: antialiased;
    }

    body, input, button {
        font-family: 'Roboto', serif;
        font-size: 16px;
    }

    h1, h2, h3, h4, h5, h6, strong {
        font-weight: 500;
    }
  
    *:focus {
      outline: 0;
    }
    
    button {
        cursor: pointer;
    }
```

Fazer a importação dos estilos globais no arquivo App.tsx


src/App.tsx
```ts
    import React from 'react';

    import GlobalStyle from './styles/global';

    const App: React.FC () => {
        return (
            <>
                <h1>Hello World</h1>
                <GlobalStyle />
            </>
        );
    }

    export default App;

```

## Utilidades do Styled

styled.button.attrs() - acessa os atributos de um elemento
```js
    const SubmitButton = styled.button.attrs(
        type: ‘submit’
    );
```

& - referer-se ao próprio elemento

&:focus – quando o elemento estiver com focus
```js
    &:focus {

    }
```

&[disabled] – quando o elemento tiver a propriedade disabled
```js
    &[disabled] {

    }
```


& + li 	- aplica a estilização em todos li meno no primeiro (precedido de um li)


Definindo o valor de um atributo baseado em uma determinada propriedade:
```js
    const SubmitButton – styled.button.attrs(props => ({
        type: ‘submit’,
        disabled: props.loading,
    }));
```


## Animações de rotação

```js
    const rotate = keyframes`
        from {
            translation: rotate(0deg);
        }

        to {
            transform: rotate(360deg);
        }
    `;
```
