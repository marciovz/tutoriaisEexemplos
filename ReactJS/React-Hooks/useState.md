# USESTATE

O hook useState permite criar estados que ao serem atualizados
provocam uma nova renderização do componente na tela.


```JS
  import React, { useState } from 'react';

  function Example() {
    const [count, setCount] = useState(0);

    return (
      <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
          Click me
        </button>
      </div>
    );
  }
```

No exemplo acima, toda vez que o button é clicado, a função setCount atualiza o estado 
da variável count, disparando uma nova renderização na tela e mostrando o novo
valor do estado count.


