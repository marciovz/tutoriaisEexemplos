## CRIANDO UM HOOK DE USERS APARTIR DE UM CONTEXTO

Mover o UserContext.tsx para pasta de hooks e alterar seu nome para useUsers.tsx

### Criando um arquivo de contexto exportando um useUsers (Hook)

src/hooks/useUsers.tsx

```tsx
import { createContext, ReactNode, useState, useContext } from "react";

interface Users {
  id: string;
  name: string;
  email: string;
}

interface UsersContext {
  users: Users;
}

const UsersContext = createContext({} as UsersContext);

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

export function useUsers() {
  const context = useContext(UsersContext);
  return context;
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
import { useUsers } from '../../hooks/useUsers';

export function Home() {
  const { users } = useUsers()

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
