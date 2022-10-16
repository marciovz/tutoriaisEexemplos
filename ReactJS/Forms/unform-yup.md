# UNFORM e Validações com YUP

### Instalando a biblioteca Unform e YUP
```cmd
$ npm install @rocketseat/unform
$ npm install yup
```

### Implementando o arquivo de formulário

```js
import { Form, Input } from ‘@rocketseat/unform’;
import * as Yup from ‘yup’;

function FormComponent() {
  const shema = Yup.object().shape({
    e-mail: Yup.string()
      .email(‘Insira um e-mail válido’)
      .required(‘O e-mail é obrigatório’),
    password: Yup.string().required(‘A senha é obrigatória’),
  });

  function handleSubmit(data) {
    console.tron.log(data);
  }

  return(
    <Form schema={schema} onSubmit={handleSubmit}>
      <Input name='email' type='email' placeholder='Seu e-mail' />
      <Input name='password' type='password' placeholder='Senha secreta' />

      <button type='submit'>Acessar</button>
    </Form>
  )
}
```