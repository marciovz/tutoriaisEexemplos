# PERMISSÕES DE ACESSO

As permissões de acesso podem ser usadas para restringir o acesso do usuário a alguma informação em uma página ou o acesso a alguma página.

## Restringindo Acesso a dados de uma página

### Criando Hook de Permissão

src/hooks/useCan.ts

```ts
import { useContext } from "react";

import { AuthContext } from "../contexts/AuthContext";
import { validateUserPermissions } from "../utils/ValidateUserPermission";

type UseCanParams = {
  permissions?: string[];
  roles?: string[];
};

export function useCan({ permissions, roles }: UseCanParams) {
  const { user, isAuthenticated } = useContext(AuthContext);

  if (!isAuthenticated) {
    return false;
  }

  const userHasValidPermissions = validateUserPermissions({
    user,
    permissions,
    roles,
  });

  return userHasValidPermissions;
}
```

### Função de Validação de Permissões

src/utils/ValidateUserPermission.ts

```ts
type User = {
  permissions: string[];
  roles: string[];
};

type ValidateUserPermissionsParams = {
  user: User;
  permissions?: string[];
  roles?: string[];
};

export function validateUserPermissions({
  user,
  permissions,
  roles,
}: ValidateUserPermissionsParams) {
  if (permissions?.length > 0) {
    const hasAllPermissions = permissions.every((permission) => {
      return user.permissions.includes(permission);
    });

    if (!hasAllPermissions) {
      return false;
    }
  }

  if (roles?.length > 0) {
    const hasAllRoles = roles.some((role) => {
      return user.roles.includes(role);
    });

    if (!hasAllRoles) {
      return false;
    }
  }

  return true;
}
```

### Criando Componente de Permissão

src/components/Can.tsx

```tsx
import { ReactNode } from "react";
import { useCan } from "../hooks/useCan";

interface CanProps {
  children: ReactNode;
  permissions?: string[];
  roles?: string[];
}

export function Can({ children, permissions, roles }: CanProps) {
  const useCanSeeComponent = useCan({ permissions, roles });

  if (!useCanSeeComponent) {
    return null;
  }

  return <>{children}</>;
}
```

### Restringindo acesso ao dados de Métricas na dashboard

src/pages/dashboard.tsx

```tsx
import { useContext, useEffect } from "react";
import { Can } from "../component/Can";

import { AuthContext } from "../contexts/AuthContext";
import { setupAPIClient } from "../services/api";
import { api } from "../services/apiClient";
import { withSSRAuth } from "../utils/withSSRAuth";

export default function dashboard() {
  const { user, signOut } = useContext(AuthContext);

  useEffect(() => {
    api
      .get("/me")
      .then((response) => console.log(response))
      .catch((err) => console.log(err));
  }, []);

  return (
    <>
      <h1>Dassboard: {user?.email}</h1>

      <button onClick={signOut}>Sign out</button>

      <Can permissions={["metrics.list"]}>
        <div>Métricas</div>
      </Can>
    </>
  );
}

export const getServerSideProps = withSSRAuth(async (context) => {
  const apiClient = setupAPIClient(context);
  await apiClient.get("/me");

  return {
    props: {},
  };
});
```

## Restringindo acesso a uma página

Restringindo o acesso a página de métricas

### Página de Métricas

src/pages/metrics.tsx

```tsx
import { setupAPIClient } from "../services/api";
import { withSSRAuth } from "../utils/withSSRAuth";

export default function Metrics() {
  return (
    <>
      <h1>Métricas</h1>
    </>
  );
}

export const getServerSideProps = withSSRAuth(
  async (context) => {
    const apiClient = setupAPIClient(context);
    const resonse = await apiClient.get("/me");

    return {
      props: {},
    };
  },
  {
    permissions: ["metrics.list"],
    roles: ["administrator"],
  }
);
```

### Função de verificação de autenticação no SSR

src/utils/withSSRAuth.ts

```ts
import {
  GetServerSideProps,
  GetServerSidePropsContext,
  GetServerSidePropsResult,
} from "next";
import { parseCookies, destroyCookie } from "nookies";
import decode from "jwt-decode";

import { AuthTokenError } from "../errors/AuthTokenError";
import { validateUserPermissions } from "./ValidateUserPermission";

type WithSSRAuthOptions = {
  permissions?: string[];
  roles?: string[];
};

export function withSSRAuth<P>(
  fn: GetServerSideProps<P>,
  options?: WithSSRAuthOptions
) {
  return async (
    context: GetServerSidePropsContext
  ): Promise<GetServerSidePropsResult<P>> => {
    const cookies = parseCookies(context);
    const token = cookies["nextauth.token"];

    if (!token) {
      return {
        redirect: {
          destination: "/",
          permanent: false,
        },
      };
    }

    if (options) {
      const user = decode<{ permissions: string[]; roles: string[] }>(token);
      const { permissions, roles } = options;

      const userHasValidPermissions = validateUserPermissions({
        user,
        permissions,
        roles,
      });

      if (!userHasValidPermissions) {
        return {
          redirect: {
            destination: "/dashboard",
            permanent: false,
          },
        };
      }
    }

    try {
      return await fn(context);
    } catch (err) {
      if (err instanceof AuthTokenError) {
        destroyCookie(context, "nextauth.token");
        destroyCookie(context, "nextauth.refreshToken");

        return {
          redirect: {
            destination: "/",
            permanent: false,
          },
        };
      }
    }
  };
}
```

### Classe de erro de Authenticação

src/errors/AuthTokenError.ts

```ts
export class AuthTokenError extends Error {
  constructor() {
    super("Error with authentication token.");
  }
}
```
