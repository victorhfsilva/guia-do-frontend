# Request Headers

## **1. User-Agent:**
   - Propósito: Identifica o agente do usuário (navegador, dispositivo, aplicativo) que está fazendo a requisição.
   - Exemplo: `User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36`

## **2. Host:**
   - Propósito: Especifica o nome de domínio do servidor a ser acessado.
   - Exemplo: `Host: www.exemplo.com`

## **3. Accept:**
   - Propósito: Indica os tipos de mídia (por exemplo, MIME types) que o cliente aceita como resposta.
   - Exemplo: `Accept: text/html, application/xhtml+xml, application/xml;q=0.9, */*;q=0.8`

## **4. Accept-Language:**
   - Propósito: Especifica as línguas preferidas pelo cliente para a resposta.
   - Exemplo: `Accept-Language: pt-BR, en-US;q=0.7`

## **5. Accept-Encoding:**
   - Propósito: Indica as codificações de conteúdo que o cliente pode entender.
   - Exemplo: `Accept-Encoding: gzip, deflate`

## **6. Authorization:**
   - Propósito: Fornece credenciais de autenticação ao servidor para acesso a recursos restritos.
   - Exemplo: `Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`

## **7. Content-Type:**
   - Propósito: Define o tipo de mídia do corpo da requisição.
   - Exemplo: `Content-Type: application/json`

## **8. Content-Length:**
   - Propósito: Indica o tamanho do corpo da requisição em bytes.
   - Exemplo: `Content-Length: 123`

## **9. Referer (ou Referer):**
   - Propósito: Indica a URL da página web anterior do qual a página atual requerida foi chamada.
   - Exemplo: `Referer: https://www.origem.com/pagina-anterior`

## **10. Cookie:**
   - Propósito: Envia cookies armazenados no navegador do cliente para identificação e estado.
   - Exemplo: `Cookie: nome=valor; outra-nome=outro-valor`

## **11. Cache-Control:**
   - Propósito: Especifica diretivas para mecanismos de cache tanto em requisições quanto em respostas
   - Exemplo: `Cache-Control: no-cache, max-age=0`

## **12. If-Modified-Since:**
   - Propósito: Permite que o cliente faça uma requisição condicional baseada na data da última modificação do recurso, o servidor enviará de volta o recurso solicitado, com um status 200, apenas se foi modificado pela ultima vez após a data fornecida.
   - Exemplo: `If-Modified-Since: Thu, 01 Jul 2021 00:00:00 GMT`

Esses são alguns dos cabeçalhos de requisição mais comuns e suas finalidades. Cabeçalhos de requisição desempenham um papel fundamental na comunicação entre o cliente e o servidor, ajudando a especificar informações importantes sobre a requisição e as preferências do cliente. É importante utilizá-los corretamente de acordo com o contexto da sua aplicação.
