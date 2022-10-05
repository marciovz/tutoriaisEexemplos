# Criando um projeto typescript com React-App

[Create React App](https://create-react-app.dev/docs/getting-started)

```cmd
$ npx create-react-app project_name --template typescript
```

### Vamos retirar os arquivos e códigos desnecessários.

Deletar os arquivos:
- public/favicon.ico
- public/logo192.png
- public/logo512.png
- public/manifest.json
- src/App.css
- src/index.css
- src/logo.svg
- src/reportWebVitais.ts
- Readme.md

Editar os seguintes arquivos:

public/index.html
```html
  <!DOCTYPE html>
  <html lang="pt-br">
    <head>
      <meta charset="utf-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1" />
      <title>Meu Site</title>
    </head>
    <body>
      <div id="root"></div>
    </body>
  </html>
```

src/App.test.tsx
```tsx
  import { render, screen } from '@testing-library/react';
  import App from './App';

  it('renders learn react link', () => {
    render(<App />);
    const linkElement = screen.getByText(/hellow world/i);
    expect(linkElement).toBeInTheDocument();
  });
```

src/App.tsx
```tsx
  function App() {
    return (
      <div>
        <p>Hellow World</p>;
      </div>
    )
  }

  export default App;
```

src/index.tsx
```tsx
  import React from 'react'
  import ReactDOM from 'react-dom/client'
  import App from './App'

  const root = ReactDOM.createRoot(
    document.getElementById('root') as HTMLElement
  );
  root.render(
    <React.StrictMode>
      <App />
    </React.StrictMode>
  );
```

## Rodar o projeto base.

```cmd
$ npm start
```