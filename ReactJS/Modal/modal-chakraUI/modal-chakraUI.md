# Componente Modal utilizado Chakra UI

### componente modal

src/components/modal/viewImage.tsx

```tsx
import {
  Modal,
  ModalOverlay,
  ModalContent,
  ModalFooter,
  ModalBody,
  Image,
  Link,
} from "@chakra-ui/react";

interface ModalViewImageProps {
  isOpen: boolean;
  onClose: () => void;
  imgUrl: string;
}

export function ModalViewImage({
  isOpen,
  onClose,
  imgUrl,
}: ModalViewImageProps): JSX.Element {
  // TODO MODAL WITH IMAGE AND EXTERNAL LINK
  return (
    <Modal isCentered onClose={onClose} isOpen={isOpen} size="4xl">
      <ModalOverlay />
      <ModalContent
        mx="auto"
        w="auto"
        h="auto"
        maxW={["300px", "500px", "900px"]}
        maxH={["350px", "450px", "600px"]}
      >
        <ModalBody p="0">
          <Image
            src={imgUrl}
            maxW={["300px", "500px", "900px"]}
            maxH={["350px", "450px", "600px"]}
          />
        </ModalBody>
        <ModalFooter bg="pGray.800" h="2rem" py="1.5rem">
          <Link href={imgUrl} isExternal fontSize="1rem">
            Abrir original
          </Link>
        </ModalFooter>
      </ModalContent>
    </Modal>
  );
}
```

### chamada para abrir o modal

```jsx
import { SimpleGrid, useDisclosure } from "@chakra-ui/react";
import { useState } from "react";
import { Card } from "./Card";
import { ModalViewImage } from "./Modal/ViewImage";

interface Card {
  title: string;
  description: string;
  url: string;
  ts: number;
  id: string;
}

interface CardsProps {
  cards: Card[];
}

export function CardList({ cards }: CardsProps): JSX.Element {
  const { isOpen, onOpen, onClose } = useDisclosure();
  const [currentImageUrl, setCurrentImageUrl] = useState("");

  function handleViewImage(url: string): void {
    onOpen();
    setCurrentImageUrl(url);
  }

  return (
    <>
      <SimpleGrid columns={[1, 2, 3]} dapcing="40px">
        {cards.map((card) => (
          <Card key={card.id} data={card} viewImage={handleViewImage} />
        ))}
      </SimpleGrid>

      <ModalViewImage
        onClose={onClose}
        isOpen={isOpen}
        imgUrl={currentImageUrl}
      />
    </>
  );
}
```
