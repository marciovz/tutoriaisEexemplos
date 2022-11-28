# MODAL COM REACT-MODAL

## Instalando a biblioteca

```cmd
$ npm install react-modal
$ npm install @types/react-modal -D
```

### instalando as dependências

```cmd
$ npm install styled-components
$ npm install @types/styled-components -D
```

### Componente Modal

```js
import { FormEvent } from "react";
import Modal from "react-modal";

import { Container } from "./styles";

interface ExampleModalProps {
  isOpen: boolean;
  onRequestClose: () => void;
}

Modal.setAppElement("#root");

export function ExampleModal({ isOpen, onRequestClose }: ExampleModalProps) {
  async function handleExampleClick(event: FormEvent) {
    event.preventDefault();
    /* ação para o clique do botão*/
    onRequestClose();
  }

  return (
    <Modal
      isOpen={isOpen}
      onRequestClose={onRequestClose}
      overlayClassName="react-modal-overlay"
      className="react-modal-content"
    >
      <button
        type="button"
        onClick={onRequestClose}
        className="react-modal-close"
      >
        X
      </button>

      <Container onSubmit={handleExampleClick}>
        <h2>Modal Example</h2>
        <button type="submit">Cadastrar</button>
      </Container>
    </Modal>
  );
}
```

### Estilização do componente modal

```css
import styled from "styled-components";

export const Container = styled.form`
  h2 {
    color: var(--text-title);
    font-size: 1.5rem;
    margin-bottom: 2rem;
  }


  button[type="submit"] {
    width: 100%;
    padding: 0 1.5rem;
    height: 4rem;
    background: var(--green);
    color: #fff;
    border-radius: 0.25rem;
    border: 0;
    font-size: 1rem;
    margin-top: 1.5rem;
    font-weight: 600;

    transition: filter 0.2s;

    &:hover {
      filter: brightness(0.9);
    }
  }
`;
```

### Estilização Global para o modal

```css
import { createGlobalStyle } from 'styled-components';

export const GlobalStyle = createGlobalStyle`
  :root {
    --background: #f0f2f5;
    --green: #33cc95;
    --text-title: #363f5f;
  }

  .react-modal-overlay {
    background: rgba(0, 0, 0, 0.5);

    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;

    display: flex;
    align-items: center;
    justify-content: center;
  }

  .react-modal-content {
    width: 100%;
    max-width: 576px;
    background: var(--background);
    padding: 3rem;
    position: relative;
    border-radius: 0.24rem;
  }

  .react-modal-close {
    position: absolute;
    right: 1.5rem;
    top: 1.5rem;
    border: 0;
    background: transparent;

    transition: filter 0.2s;

    &:hover {
      filter: brightness(0.8);
    }
  }
`;
```

### Utilizando o modal

```js
import { useState } from "react";

import { ExampleModal } from "./components/ExampleModal";

import { GlobalStyle } from "./styles/global";

export function App() {
  const [isExampleModalOpen, setIsExampleModalOpen] = useState(false);

  function handleOpenExampleModal() {
    setIsExampleModalOpen(true);
  }

  function handleCloseExampleModal() {
    setIsExampleModalOpen(false);
  }

  return (
    <div>
      <button type='button' onClick={handleOpenExampleModal}>Open Modal<button />
      <ExampleModal
        isOpen={isExampleModalOpen}
        onRequestClose={handleCloseExampleModal}
      />
      <GlobalStyle />
    </div>
  );
}
```
