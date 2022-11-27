# FAKE API COM JSON SERVER

### Instalar a biblioteca json-server
```cmd
$ npm install json-server -D
```

### Implementar o arquivo de dados na raiz do projeto
server.json
```json
"user": [
  {
    "id": "001",
    "name": "João da Silva",
    "emal": "joao.silva@email.com",
    "password": "123456"
  },
    {
    "id": "002",
    "name": "Maria Joaquina",
    "emal": "maria.joaquina@email.com",
    "password": "234567"
  },
  {
    "id": "003",
    "name": "Paulo Soares",
    "emal": "paulo.soares@email.com",
    "password": "345678"
  },
]
```

### Rodar a aplicação
```cmd
$ npx json-server server.json -p 3001 -w
```
