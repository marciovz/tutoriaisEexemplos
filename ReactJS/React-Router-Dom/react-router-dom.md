# Trabalhando com rotas no ReactJS

### Instalando a biblioteca react-router-dom
```cmd
$ npm install react-router-dom
```

### Criando duas páginas de exemplo para fazer o roteamento.

src/pages/Home.tsx
```tsx
  export function Home() {
    return <h1>Home</h1>
  }
```

src/pages/About.tsx
```tsx
  export function About() {
    return <h1>About</h1>
  }
```

### Criando um arquivo de rota.

src/Router.tsx
```tsx
  import { Routes, Route } from 'react-router-dom'
  import { Home } from './pages/Home'
  import { About } from './pages/About'

  export function Router() {
    return (
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    )
  }
```

### Adicionando o BrowserRouter no arquivo App

src/App.tsx
```tsx
  import { BrowserRouter } from 'react-router-dom'
  import { Router } from './Router'

  export function app() {
    return (
      <BrowserRouter>
        <Router />
      </BrowserRouter>
    )
  }
```

# Usando Estrutura de Layouts

Com a estrutura de layout podemos definir uma estrutura stática, cabendo ao router trocar apenas o componente que deve mudar na estrutura.

Nesse exemplo o componente Header estará em todas as rotas.

src/components/Header.tsx
```tsx
  export function Header() {
    return <h1>Header</h1>
  }
```

src/layouts/DefaultLayout.tsx
```tsx
  import { Outlet } from 'react-router-dom'
  import {Header } from '../components/Header'

  export function DefaultLayout() {
    return (
      <div>
        <Header />
        <Outlet />
      </div>
    )
  }
```

src/Routes.tsx
```tsx
  import { Routes, Route } from 'react-router-dom'
  import { DefaultLayout } from './layouts/DefaultLayout'
  import { Home } from './pages/Home'
  import { About } from './pages/About'

  export function Router() {
    return (
      <Routes>
        <Route path="/" element={<DefaultLayout />} />
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
        <Route>
      </Routes>
    )
  }
```
Nesse contexto o componente Home ou o componente About será renderizado no lugar do elemento Outlet.