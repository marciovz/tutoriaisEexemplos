# MEMO

O MEMO faz uma verificação no componente, e verifica se suas propriedades e estados foram alterados.
Caso não tenha nenhuma modificação, esse componente no entrará na lista de renderização.

Utilizar o memo():
- em componentes funcionais puros;
- que renderizam com muita frequência;
- que renderizam sempre com as mesmas propriedades;
- em componentes de tamanho médio a grandes;

```js
  import { memo } from 'react'

  type ItemProps = {
    title: string
  }

  function ItemComponent(props: ItemProps) {
    return <li>{props.title}</li>
  }

  export const Item = memo(ItemComponent)
```


Fluxo de Renderização - O react cria uma nova dom para cada elemento e compara com a dom anterior para verificar se houve alguma alteração no item.

A função memo() utiliza de comparação raza, onde a comparação de dois objetos apenas será verdadeira se elas tiverem a mesma referencia. Para esses casos utilizamos useMemo e useCallback para evitar que as funções e variáveis sejam reescritas e tenham suas referencias alteradas.


Referências

[Rocketseat - youtube](https://www.youtube.com/watch?v=NmU2nNehNNY)
