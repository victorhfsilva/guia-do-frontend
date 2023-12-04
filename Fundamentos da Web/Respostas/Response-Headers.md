# Response Headers

## **1. Content-Type:**
   - Propósito: Define o tipo de mídia (por exemplo, MIME type) do conteúdo da resposta.
   - Exemplo: `Content-Type: application/json`

## **2. Content-Length:**
   - Propósito: Indica o tamanho do conteúdo da resposta em bytes.
   - Exemplo: `Content-Length: 123`

## **3. Cache-Control:**
   - Propósito: Define instruções de cache para intermediários e o navegador.
   - Exemplo: `Cache-Control: no-cache, max-age=0`

## **4. Server:**
   - Propósito: Informa o nome e versão do servidor web que respondeu à requisição.
   - Exemplo: `Server: Apache/2.4.41 (Unix)`

## **5. Last-Modified:**
   - Propósito: Indica a data e hora da última modificação do recurso.
   - Exemplo: `Last-Modified: Tue, 01 Jul 2021 00:00:00 GMT`

## **6. ETag:**
   - Propósito: Fornece um identificador para uma versão específica de um recurso. A ETag permite que o cache torne-se mais eficiente e preserve o tráfego de dados, assim um web server não precisa reenviar uma resposta com todos os dados que não tiveram nenhuma mudança em seu conteúdo.
   - Exemplo: `ETag: "12345"`

## **7. Location:**
   - Propósito: Usado em redirecionamentos (códigos de status 3xx) para especificar a URL para a qual o cliente deve ser redirecionado.
   - Exemplo: `Location: https://www.novourl.com`

## **8. Access-Control-Allow-Origin:**
   - Propósito: Usado em requisições CORS para especificar quais origens têm permissão para acessar o recurso.
   - Exemplo: `Access-Control-Allow-Origin: https://www.origempermitida.com`

## **9. Set-Cookie:**
   - Propósito: Envia cookies para serem armazenados no navegador do cliente para identificação e estado.
   - Exemplo: `Set-Cookie: nome=valor; HttpOnly; Secure`

## **10. WWW-Authenticate:**
   - Propósito: Usado em respostas 401 (Unauthorized) para indicar o método de autenticação que o cliente deve usar.
   - Exemplo: `WWW-Authenticate: Basic realm="Autenticação necessária"`


Estes são alguns dos cabeçalhos de resposta mais comuns e suas finalidades. Os cabeçalhos de resposta desempenham um papel fundamental na comunicação entre o servidor e o cliente, fornecendo informações importantes sobre o conteúdo, a autenticação e as instruções de cache. É importante utilizá-los corretamente de acordo com o contexto da sua aplicação.
