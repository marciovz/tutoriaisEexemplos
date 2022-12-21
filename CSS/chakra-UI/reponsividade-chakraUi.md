# RESPONSIVIDADE NO CHAKRA-UI

## BreakPoints

### Array

Podemos definir os valores de cada breakpoint através de array

[ sm, md, lg, xl, 2xl, ... ]

### Object

Podemos definir os valores de cada breakpoint através de objeto

{ sm: '10', md: '16', lg: '18', xl: '22' }

## Hooks

### useBreakPointValue

Podemos definir valores em variáveis controladas pelo valor do breakpoint atual.

```js
fucntion Example() {
  const variant = useBreakPointValue({ base: "outline", md: "solid" })

  return (
    <VStack align="flex-start">
      <Text>Resize your window to see the button variant change</Text>
      <Button colorScheme="teal" variant={variant}>
        Button
      </Button>
    </VStack>
  )
}
```

### useMediaQuery

Podemos definir variáveis dependendo do valor da media query

```js
function Example() {
  const [isLargerThan1280] = useMediaQuery("(min-width: 1280px)");

  return (
    <Text>
      {isLargerThan1280 ? "larger than 1280px" : "smaller than 1280px"}
    </Text>
  );
}
```

### Alterando a configuração dos breakpoints

O chakra possui os breakpoints padrões, mas se for necessário podemos alterá-los inserindo as configuração abaixo:

src/styles/themes.ts

```ts
import { createBreakpoints } from "@chakra-ui/theme-tools";

const breakpoints = createBreakpoints({
  sm: "30em",
  md: "48em",
  lg: "62em",
  xl: "80em",
  "2xl": "96em",
});
```

## Definindo tamanho da fonte conforme resolução da tela

Aqui estamos definindo o tamanho da fonte para "2xl" na resolução sm, e a partir da resolução sm o tamanho da fonte passa a ser "3xl"

```tsx
import { Text } from "@chakra-ui/react";

export function Logo() {
  return (
    <Text
      fontSize={["2xl", "3xl"]} // xl="2xl", md="3xl"
      fontWeight="bold"
      letterSpacing="tight"
      w="64"
    >
      dashgo
      <Text as="span" ml="1" color="pink.500">
        .
      </Text>
    </Text>
  );
}
```
