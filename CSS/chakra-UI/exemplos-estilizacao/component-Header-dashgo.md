# COMPONENTE HEADER DASHGO

Componente Header <br>
Projeto Dashgo <br>
Ignite 2021 <br>

![Header DashGo](./assets/componente-header-dashgo.png)

src/components/Header.tsx

```tsx
import { Flex, useBreakpointValue, IconButton, Icon } from "@chakra-ui/react";

import { useSidebarDrawer } from "../../contexts/SidebarDrawerContext";
import { NotificationsNav } from "./NotificationsNav";
import { Profile } from "./Profile";
import { SearchBox } from "./SearchBox";
import { Logo } from "./Logo";
import { RiMenuLine } from "react-icons/ri";

export function Header() {
  const { onOpen } = useSidebarDrawer();

  const isWideVersion = useBreakpointValue({
    base: false,
    lg: true,
  });

  return (
    <Flex
      as="header"
      w="100%"
      maxWidth={1480}
      h="20"
      mx="auto"
      mt="4"
      px="6"
      align="center"
    >
      {!isWideVersion && (
        <IconButton
          aria-label="Open navigation"
          icon={<Icon as={RiMenuLine} />}
          fontSize="24"
          variant="unstyle"
          onClick={onOpen}
          mr="2"
        ></IconButton>
      )}

      <Logo />

      {isWideVersion && <SearchBox />}

      <Flex align="center" ml="auto">
        <NotificationsNav />
        <Profile showProfileData={isWideVersion} />
      </Flex>
    </Flex>
  );
}
```
