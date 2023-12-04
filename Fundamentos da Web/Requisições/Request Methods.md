# Request Methods

## **GET**

- Usado para recuperar dados de um servidor.
- Não deve ter efeito colateral no servidor.
- Os dados são geralmente enviados na URL. (Cheque [Query String vs Path Parameter](./Query%20String%20vs%20Path%20Parameter.md))
- Pode ser armazenado em cache pelo navegador.

Exemplo:
```http
GET /api/users
```

## **POST**

- Usado para enviar dados para o servidor.
- Pode ter efeito colateral no servidor, como a criação de um novo recurso.
- Os dados são enviados no corpo da requisição.
- Não é armazenado em cache pelo navegador.

Exemplo:
```http
POST /api/users
```

## **PUT**

- Usado para atualizar dados existentes no servidor.
- Os dados são enviados no corpo da requisição e substituem completamente os dados existentes.
- Deve ser idempotente, o que significa que a mesma requisição pode ser feita várias vezes sem efeitos colaterais diferentes.

Exemplo:
```http
PUT /api/users/123
```

## **PATCH**

- Usado para fazer atualizações parciais em um recurso no servidor.
- Os dados são enviados no corpo da requisição e são aplicados apenas às partes específicas do recurso.
- Enquanto o PUT permite apenas substituições completas o Patch aplica modificações parciais.
- Ao contrário do PUT, o PATCH não é idempotente, requisições sucessivas idênticas podem obter efeitos distintos.

Exemplo:
```http
PATCH /api/users/123
```

## **DELETE**

- Usado para solicitar a remoção de um recurso no servidor.
- Deve ser idempotente.
- Geralmente não envia dados no corpo da requisição.

Exemplo:
```http
DELETE /api/users/123
```

## **HEAD**

- Similar ao GET, mas solicita apenas os cabeçalhos da resposta, não o corpo.
- Útil para verificar informações sobre um recurso, como verificar se ele existe ou verificar os cabeçalhos de resposta.

Exemplo:
```http
HEAD /api/users/123
```

## **OPTIONS**

- Solicita informações sobre as opções de comunicação disponíveis para um recurso, como os métodos de requisição permitidos. (Cheque [CORS](CORS.md))

Exemplo:
```http
OPTIONS /api/users
```

Estes são os métodos de requisição HTTP mais comuns. Eles permitem que os clientes se comuniquem com servidores web de diversas maneiras para realizar operações em recursos. Cada método tem seu propósito e comportamento específico, e é importante escolher o método apropriado para a tarefa que você deseja executar.