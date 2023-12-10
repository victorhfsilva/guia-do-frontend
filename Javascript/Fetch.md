# **`fetch` em JavaScript**

O `fetch` é uma API que permite fazer solicitações de rede, como buscar dados de uma API REST ou carregar recursos de um servidor. Aqui estão os principais conceitos:

## **Realizar uma Solicitação GET:**

   ```javascript
   fetch('https://api.example.com/data')
     .then((response) => {
       if (!response.ok) {
         throw new Error('Erro na solicitação');
       }
       return response.json();
     })
     .then((data) => {
       console.log(data);
     })
     .catch((erro) => {
       console.error(erro);
     });
   ```

   Use o `fetch` para fazer uma solicitação GET para a URL fornecida. Lide com a resposta em promessas usando `.then()`.

## **Enviar Dados com uma Solicitação POST:**

   ```javascript
   fetch('https://api.example.com/enviar', {
     method: 'POST',
     body: JSON.stringify({ nome: 'Exemplo' }),
     headers: {
       'Content-Type': 'application/json',
     },
   })
     .then((response) => {
       if (!response.ok) {
         throw new Error('Erro na solicitação');
       }
       return response.json();
     })
     .then((data) => {
       console.log(data);
     })
     .catch((erro) => {
       console.error(erro);
     });
   ```

   Para enviar dados com uma solicitação POST, especifique o método, o corpo da solicitação e cabeçalhos apropriados.

## **Tratar Respostas JSON:**

   ```javascript
   fetch('https://api.example.com/data')
     .then((response) => {
       if (!response.ok) {
         throw new Error('Erro na solicitação');
       }
       return response.json();
     })
     .then((data) => {
       console.log(data);
     })
     .catch((erro) => {
       console.error(erro);
     });
   ```

   Use `.json()` para analisar respostas JSON em um objeto JavaScript.

## **Lidar com Respostas de Texto:**

   ```javascript
   fetch('https://api.example.com/texto')
     .then((response) => {
       if (!response.ok) {
         throw new Error('Erro na solicitação');
       }
       return response.text();
     })
     .then((texto) => {
       console.log(texto);
     })
     .catch((erro) => {
       console.error(erro);
     });
   ```

   Use `.text()` para obter o conteúdo da resposta como uma string.

## **Configuração de Cabeçalhos Personalizados:**

   ```javascript
   fetch('https://api.example.com/data', {
     headers: {
       'Authorization': 'Bearer Token',
     },
   })
     .then((response) => {
       // ...
     });
   ```

   Personalize cabeçalhos da solicitação, como autorização ou outros cabeçalhos específicos do aplicativo.

## **`async/await` com `fetch`:**

   ```javascript
   async function fetchData() {
     try {
       const response = await fetch('https://api.example.com/data');
       if (!response.ok) {
         throw new Error('Erro na solicitação');
       }
       const data = await response.json();
       console.log(data);
     } catch (erro) {
       console.error(erro);
     }
   }

   fetchData();
   ```

   Você também pode usar `async/await` para tornar o código mais legível quando se trabalha com `fetch`.

## **Solicitações de Cross-Origin:**

   Esteja ciente das políticas de segurança de mesma origem (Same-Origin) ao fazer solicitações de Cross-Origin. Use cabeçalhos CORS ou um proxy de servidor se necessário.
