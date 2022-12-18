# ACTIVE LINK

o componente ActiveLink é um Wrapper para links que sinaliza um link quando ele estiver ativo, ou seja, quando a página ativa corresponde ao path do link.

### Componente ActiveLink

components/ActiveLink/index.tsx

```tsx
import { useRouter } from "next/router";
import Link, { LinkProps } from "next/link";
import { ReactElement, cloneElement } from "react";

interface ActiveLinkProps extends LinkProps {
  children: ReactElement;
  activeClassName: string;
}

export function ActiveLink({
  children,
  activeClassName,
  ...rest
}: ActiveLinkProps) {
  const { asPath } = useRouter();

  const className = asPath === rest.href ? activeClassName : "";

  return <Link {...rest}>{cloneElement(children, { className })}</Link>;
}
```

### Usando o componente ActiveLink

Exemplo de uso do componente ActiveLink

components/Header/index.tsx

```tsx
import { SignInButton } from "../SignInButton";

import styles from "./styles.module.scss";
import { ActiveLink } from "../ActiveLink";

export function Header() {
  return (
    <header className={styles.headerContainer}>
      <div className={styles.headerContent}>
        <img src="/images/logo.svg" alt="ig.news" />
        <nav>
          <ActiveLink activeClassName={styles.active} href="/">
            <a>Home</a>
          </ActiveLink>
          <ActiveLink activeClassName={styles.active} href="/posts">
            <a>Posts</a>
          </ActiveLink>
        </nav>

        <SignInButton />
      </div>
    </header>
  );
}
```
