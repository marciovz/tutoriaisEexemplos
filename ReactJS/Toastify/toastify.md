# TRATAMENTO DE ERROS COM TOASTIFY

### Instalar a biblioteca do react-toastify
```cmd
  $ npm install react-toastify
```

### Inicializar a biblioteca no arquivo app.js
src/App.js
```js
  import { ToastContainer } from 'react-toastify'

  . . . 

  <ToastContainer autoClose={3000} />
```

### Adicionar a estilização do toastify no arquivo de estilo global da aplicação
src/styles/global.css
```js
  import 'react-toastify/dist/ReactToastify.css'

  . . . 

```

### Chamando uma mensagem com toastify

```js
  import { toast } from 'react-toastify'

  . . . 

  catch(err) {
    toast.error('Ocorreu um erro ...')
  }
```