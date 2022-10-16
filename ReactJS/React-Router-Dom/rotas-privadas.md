# ROTAS PRIVADAS

### Arquivo de roteamento
src/routes/index.tsx
```tsx
import { Routes, Route } from 'react-router-dom'

import { PrivateRoute } from './PrivateRoute'
import { Auth } from '../pages/Auth'
import { Home } from '../pages/Home'


export function Router() {
  return (
    <Routes>
      <Route path='/login' element={<Auth />} />
      
      <Route path='/' element={
        <PrivateRoute redirectTo='/login'>
          <Home />
        </PrivateRoute>} 
      />
      
    </Routes>
  )
}
```


### Criar o arquivo para verificação de usuário authenticado

src/routes/PrivateRoute.tsx
```tsx
import { ReactElement, useContext } from "react";
import { Navigate } from 'react-router-dom'

import { AuthContext } from '../contexts/AuthContext'

interface PrivateRouteProps {
  children: ReactElement
  redirectTo: string
}

export function PrivateRoute({ children, redirectTo }: PrivateRouteProps) {
  const { isAuthenticated, loading } = useContext(AuthContext);

  if (loading) {
    return <div className='loading'>...Carregando...</div>
  }

  if (!isAuthenticated) {
    return <Navigate to={redirectTo} />
  } 

  return children
}

```

### Arquivo de contexto de Autenticação
src/context/AuthContext.tsx
```tsx
import { createContext, ReactNode, useEffect, useState } from 'react';
import { useNavigate } from 'react-router-dom';

import { api, createSession } from '../services/api'


interface User {
  name: string;
  email: string;
  password: string;
}

interface LoginProps {
  email: string;
  password: string;
}

interface Auth {
  isAuthenticated: boolean;
  user: User;
}

interface AuthContextType {
  user: User | null;
  loading: boolean;
  isAuthenticated: boolean;
  login: ({ email, password }: LoginProps) => void;
  logout: () => void;
}

export const AuthContext = createContext({} as AuthContextType);

interface AuthContextProviderProps {
  children: ReactNode
}

export function AuthContextProvider({ children }: AuthContextProviderProps) {
  const [ user, setUser ] = useState<User | null>(null);
  const [ loading, setLoading] = useState(true);

  const navigate = useNavigate();

  useEffect(() => {
    const recoveredUser = localStorage.getItem('user');
    const token = localStorage.getItem('token');

    if (recoveredUser && token) {
      setUser(JSON.parse(recoveredUser));
      api.defaults.headers.Authorization = `Bearer ${token}`;
    }
    setLoading(false);
  }, [])

  async function login({ email, password }: LoginProps) {
    const response = await createSession({ email, password });

    const loggedUser = response.data.user;
    const token = response.data.token
    
    localStorage.setItem("user", JSON.stringify(loggedUser));
    localStorage.setItem("token", token);

    api.defaults.headers.Authorization = `Bearer ${token}`;
    setUser(loggedUser);
    navigate('/');
  }

  function logout() {
    api.defaults.headers.Authorization = null;
    localStorage.removeItem('user')
    setUser(null);
    navigate('/login');
  }

  return (
    <AuthContext.Provider 
      value={{
        loading,
        isAuthenticated: !!user,
        login,
        logout,
        user
      }}
    >
      {children}
    </AuthContext.Provider>
  )
}

```

### Adicionando o Provider de Autorização no arquivo App.tsx

src/app.tsx
```tsx
import { BrowserRouter } from 'react-router-dom'

import { AuthContextProvider } from './contexts/AuthContext';
import { Router } from './routes'

import './styles/global.css';

function App() {

  return (
    <BrowserRouter>
      <AuthContextProvider>
        <Router />
      </AuthContextProvider>
    </BrowserRouter>
  )
}

export default App

```

### Serviço de API com Axios

src/services/Api.ts
```tsx
import axios from 'axios'

export const api = axios.create({
  baseURL: "http://localhost:3000"
})

interface CreateSessionProps {
  email: string;
  password: string;
}

export const createSession = async ({ email, password }: CreateSessionProps) => {
  return api.post('/sessions', { email, password })
}
```


### Página de login

src/pages/Auth.tsx
```tsx
import { FormEvent, useState, useContext } from "react";

import { AuthContext } from "../../contexts/AuthContext";

import './styles.css';

export function Auth() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  const { isAuthenticated, login } = useContext(AuthContext)

  const handleSubmit = (event: FormEvent) => {
    event.preventDefault();
    login({ email, password })
  }

  return (
    <main id="login">
      <h1 className="title">Login do sistema</h1>
      <p>{isAuthenticated? 'true' : 'false'}</p>
      <form onSubmit={handleSubmit}>
        <fieldset>
          <label htmlFor="email">
            Email
            <input 
              id='email' 
              type='email' 
              name='email' 
              value={email} 
              onChange={e => setEmail(e.target.value)}
            />
          </label>

          <label htmlFor="password">
            Password
            <input 
              id='password' 
              type='password' 
              name='password' 
              value={password} 
              onChange={e => setPassword(e.target.value)} 
            />
          </label>

          <button type='submit'>Login</button>
        </fieldset>
      </form>
    </main>
  )
}

```

### Página Home
src/pages/Home.tsx
```tsx
import { useContext } from "react"
import { Link } from "react-router-dom"

import { AuthContext } from "../contexts/AuthContext"

export function Home() {
  const { user, logout } = useContext(AuthContext)

function handleLogout() {
  logout()
}

  return(
    <>
      <h1>Page Home</h1>
      <Link to='/login'>Login</Link>
      <button onClick={handleLogout}>Logout</button>
      {!user ? (
        <p>Nenhum usuário logado</p>
      ) : (
        <>
          <p>{user.name}</p>
          <p>{user.email}</p>
          <p>{user.password}</p>
        </>
      )}
    </>
  )
}

```