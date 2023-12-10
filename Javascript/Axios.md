# **Axios**

Axios é uma biblioteca JavaScript amplamente utilizada para fazer solicitações HTTP a servidores a partir de navegadores e Node.js. Aqui estão os conceitos e recursos essenciais da Axios:

## **Instalação:**

   Para utilização no projeto, instale o Axios via npm ou yarn:

   ```
   npm install axios
   ```

   Importe o Axios em seu código:

   ```javascript
   const axios = require('axios'); // Node.js
   // ou
   import axios from 'axios'; // Navegador
   ```

## **Realizar uma Requisição GET:**

   ```javascript
   axios.get('https://api.example.com/data')
     .then((response) => {
       console.log(response.data);
     })
     .catch((error) => {
       console.error(error);
     });
   ```

## **Realizar uma Requisição POST:**

   ```javascript
   axios.post('https://api.example.com/enviar', { nome: 'Exemplo' })
     .then((response) => {
       console.log(response.data);
     })
     .catch((error) => {
       console.error(error);
     });
   ```

## **Configuração de Cabeçalhos:**

   ```javascript
   axios.get('https://api.example.com/data', {
     headers: {
       'Authorization': 'Bearer Token',
     },
   })
     .then((response) => {
       // ...
     });
   ```

  ```javascript
   axios.post('https://api.example.com/enviar', { nome: 'Exemplo' }, {
     headers: {
       'Authorization': 'Bearer Token',
     }
    })
     .then((response) => {
       const data = response.data;
       console.log(data);
     })
     .catch((error) => {
       console.error(error);
     });
   ```

## **Configuração Global de BaseURL:**

   Você pode definir um URL base para todas as solicitações Axios:

   ```javascript
   const instance = axios.create({
     baseURL: 'https://api.example.com/',
   });

   instance.get('/data').then(/*...*/);
   ```

   Também é possível definir timeout e headers base:

  ```javascript
  const instance = axios.create({
    baseURL: 'https://some-domain.com/api/',
    timeout: 1000,
    headers: {'X-Custom-Header': 'foobar'}
  }); 
  ```

## **Cancelamento de Solicitações:**

   Axios suporta cancelamento de solicitações usando o signal. Isso é útil para evitar chamadas desnecessárias.

   ```javascript
    const controller = new AbortController();

    axios.get('/foo/bar', {
      signal: controller.signal
    }).then(function(response) {
      //...
    });

    // cancela a requisição
    controller.abort()
   ```

   ```javascript
   axios.get('/foo/bar', {
      signal: AbortSignal.timeout(5000) //Aborta a requisição após 5 segundos
    }).then(function(response) {
      //...
    });
   ```

## **`async/await` com Axios:**

    Você pode usar `async/await` para simplificar o código e torná-lo mais legível:

    ```javascript
    async function fetchData() {
      try {
        const response = await axios.get('https://api.example.com/data');
        const data = response.data;
        console.log(data);
      } catch (error) {
        console.error(error);
      }
    }

    fetchData();
    ```

## Mais Informações

[Axios-HTTP](https://axios-http.com/)

Axios é uma poderosa biblioteca para fazer solicitações HTTP em JavaScript. Ela fornece muitos recursos para simplificar o trabalho com APIs e recursos da web. Use Axios para buscar e enviar dados, adicionar autenticação e lidar com erros de maneira eficaz.