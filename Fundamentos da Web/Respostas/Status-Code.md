# Status Code

## **1xx - Informacional:**

- **100 - Continue:** Indica que o servidor recebeu a requisição inicialmente e o cliente pode continuar com a requisição.

- **101 - Switching Protocols:** Indica que o servidor concorda em mudar o protocolo solicitado pelo cliente.

## **2xx - Sucesso:**

- **200 - OK:** A requisição foi bem-sucedida, e o servidor retorna os dados solicitados.

- **201 - Created:** Indica que a requisição resultou na criação de um novo recurso.

- **204 - No Content:** A requisição foi bem-sucedida, mas não há conteúdo para retornar (usado frequentemente em requisições DELETE).

## **3xx - Redirecionamento:**

- **301 - Moved Permanently:** Indica que o recurso solicitado foi permanentemente movido para uma nova URL.

- **302 - Found (ou Moved Temporarily):** Indica que o recurso foi temporariamente movido para uma nova URL.

- **304 - Not Modified:** Indica que o recurso não foi modificado desde a última requisição.

## **4xx - Erro do Cliente:**

- **400 - Bad Request:** Indica que a requisição foi malformada ou contém parâmetros inválidos.

- **401 - Unauthorized:** Indica que a autenticação é necessária, e as credenciais fornecidas são inválidas.

- **403 - Forbidden:** O servidor entende a requisição, mas o acesso ao recurso é proibido.

- **404 - Not Found:** O recurso solicitado não foi encontrado no servidor.

- **429 - Too Many Requests:** Indica que o cliente atingiu o limite de requisições em um determinado período de tempo (rate limit).

## **5xx - Erro do Servidor:**

- **500 - Internal Server Error:** Indica um erro interno no servidor que impede que ele atenda à requisição.

- **502 - Bad Gateway:** Indica que um servidor intermediário (gateway) recebeu uma resposta inválida do servidor de origem.

- **503 - Service Unavailable:** Indica que o servidor não está disponível no momento, geralmente devido a sobrecarga ou manutenção.

- **504 - Gateway Timeout:** Indica que um servidor intermediário (gateway) não recebeu uma resposta a tempo do servidor de origem.
