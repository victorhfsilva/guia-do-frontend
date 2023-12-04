# **CORS (Cross-Origin Resource Sharing) Cheatsheet:**

## **1. O que é CORS?**
   - CORS é um mecanismo de segurança utilizado pelos navegadores para controlar as requisições HTTP entre diferentes origens (domínios).

## **2. Como Funciona:**
   - Navegadores impõem a política de mesma origem (Same-Origin Policy) por padrão.
   - CORS permite que um servidor especifique quem pode acessar seus recursos.

## **3. Cabeçalhos CORS Principais:**
   - **Origin:** Indica a origem da requisição.
   - **Access-Control-Allow-Origin:** Especifica quais origens têm permissão para acessar os recursos.
   - **Access-Control-Allow-Methods:** Define os métodos HTTP permitidos.
   - **Access-Control-Allow-Headers:** Lista os cabeçalhos HTTP permitidos.
   - **Access-Control-Allow-Credentials:** Indica se as credenciais (como cookies) podem ser enviadas.

## **4. Tipos de Requisições CORS:**
   - **Simples:** GET, HEAD, POST (com certas condições).
   - **Não-Simples:** Requisições que desencadeiam o pré-envio de um OPTIONS e, após a "aprovação", o servidor envia a requisição verdadeira com o método de requisição HTTP correto.

## **5. Requisições com Pré-envio:**
   - Requisições com pré-envio primeiramente enviam uma requisição HTTP através do método OPTIONS a fim de determinar se de fato a requisição atual é segura para envio.
   - O servidor então responde com cabeçalhos CORS que indicam as permissões (Access-Control-*) desta origem.
   - Uma vez que a requisição com pré-envio é completa, só então a requisição efetiva será enviada.

## **6. Exemplo de Cabeçalhos CORS:**
   ```http
   Access-Control-Allow-Origin: https://dominio-permitido.com
   Access-Control-Allow-Methods: GET, POST, OPTIONS
   Access-Control-Allow-Headers: Content-Type
   Access-Control-Allow-Credentials: true
   ```

## **7. Configurações do Servidor:**
   - Configurar o servidor para incluir cabeçalhos CORS apropriados.
   - Garantir que a política de mesmo origem esteja configurada corretamente.

## **8. Recursos:**
   - [CORS: Mdn Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/CORS)

Lembre-se de que a implementação de CORS varia dependendo do servidor e do contexto específico.