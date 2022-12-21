# React Hook Form

### Instalando a biblioteca react-hook-form.

```cmd
$ npm install react-hook-form
```

### Criando um formulário não controlado.

```tsx
  import { useForm } form 'react-hook-form'

  export function Home() {
    const { register, handleSubmit, watch, formState } = useForm()
    const { errors } = formState

    const name = watch('name')
    const email = watch('email')
    const isSubmitDisable = !name ||!email

    function handleSubmit(data) {
      if( errors ) {
        console.log(errors)
      }
      console.log(data)
    }

    return (
      <form onSubmit={handleSubmit}>
        <input
          placeholder="Digite seu nome"
          {...register('name')}
        />
        <input
          placeholder="Digite seu email"
          {...register('email')}
        />
        <button
          type="submit"
          disabled={isSubmitDisabled}
        >
          Enviar
        </button>
      </form>
    )
  }
```
