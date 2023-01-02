# MEMO

O MEMO faz uma verificação no componente, e verifica se suas propriedades e estados foram alterados.
Caso não tenha nenhuma modificação, esse componente no entrará na lista de renderização.

### Fluxo de renderização do React

1.  Criar uma nova versão do componente
2.  Comparar com a versão anterior
3.  Se houverem alterações, vai atualizar o que alterou

### Quando utilizar o memo

- em componentes funcionais puros;
- que renderizam com muita frequência;
- que renderizam sempre com as mesmas propriedades;
- em componentes de tamanho médio a grandes;

### Código de exemplo de uso simples

```js
import { memo } from "react";

type ItemProps = {
  title: string,
};

function ItemComponent(props: ItemProps) {
  return <li>{props.title}</li>;
}

export const Item = memo(ItemComponent);
```

Fluxo de Renderização - O react cria uma nova dom para cada elemento e compara com a dom anterior para verificar se houve alguma alteração no item.

A função memo() utiliza de comparação raza, onde a comparação de dois objetos apenas será verdadeira se elas tiverem a mesma referencia. Para esses casos utilizamos useMemo e useCallback para evitar que as funções e variáveis sejam reescritas e tenham suas referencias alteradas.

Referências

[Rocketseat - youtube](https://www.youtube.com/watch?v=NmU2nNehNNY)

### Exemplo de uso recebendo objetos como parâmetros

Quando o componente recebe objetos como parâmetro, o componente sempre renderizará novamente porque uma comparação raza de dois objetos sempre volta como false (diferente);
Para esses casos podemos passar um segundo parâmetro para o Hook memo fazer a comparação no lugar da compraração raza.

```tsx
import { memo } from "react";

interface productItemProps {
  product: {
    id: number;
    price: number;
    title: string;
  };
}

function ProductItemComponent({ product }) {
  return (
    <div>
      {product.title} - <strong> {product.price}</strong>
    </div>
  );
}

export const ProductItem = memo(
  ProductitemComponent,
  (prevProps, nextProps) => {
    // compara se possuem as mesmas propriedades e valores.
    return Object.is(prevProps.product, nextProps.product);
  }
);
```
