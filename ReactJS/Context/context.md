# CONTEXT

É a forma de disponibilizar dados pela aplicação em tempo real.

### Criando um arquivo de contexto

src/contexts/UserContext.tsx

```tsx
import { createContext, ReactNode, useState } from "react";

interface Users {
  id: string;
  name: string;
  email: string;
}

interface UsersContext {
  users: Users;
}

export const UsersContext = createContext({} as UsersContext);

interface UsersProviderProps {
  children: ReactNode;
}

export function UsersProvider({ children }: UsersProviderProps) {
  const [users, setUsers] = useState<Users>([]);

  return (
    <UsersContext.provider
      value={{
        users,
      }}
    >
      {children}
    </UsersContext.provider>
  );
}
```

### Disponibilizando o contexto na aplicação

```tsx
import { Router } from "./Router";
import { UsersProvider } from "./contexts/UsersContext";

export function App() {
  return (
    <UsersProvider>
      <Router />
    </UsersProvider>
  );
}
```

### Acessando o contexto nas páginas

```tsx
import { useContext } from 'react';
import { UserContext } from '../../contexts/UsersContext';

export function Home() {
  const { users } = useContext(UsersContext)

  return(
    {
      users.map(user => (
        <div key={user.id}>
          <p>user.id</p>
          <p>user.name</p>
          <p>user.email</p>
        </div>
      ))
    }
  )
}
```
