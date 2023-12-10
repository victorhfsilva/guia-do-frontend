# **Funções Assíncronas**

Funções assíncronas permitem lidar com operações assíncronas de forma mais legível e eficiente usando a palavra-chave `async`. Aqui estão os principais conceitos:

## **Definindo Funções Assíncronas:**

   Para criar uma função assíncrona, use a palavra-chave `async` antes da função:

   ```javascript
   async function minhaFuncaoAssincrona() {
     // Código assíncrono aqui
   }
   ```

## **`await` para Esperar Promessas:**

   Use a palavra-chave `await` dentro de funções assíncronas para aguardar a resolução de promessas. Isso faz com que o código aguarde até que a promessa seja resolvida ou rejeitada.

   ```javascript
   async function exemplo() {
     const resultado = await algumaPromessa();
     console.log(resultado);
   }
   ```

## **Tratamento de Erros:**

   Use `try...catch` para tratar erros ao usar `await`:

   ```javascript
   async function exemplo() {
     try {
       const resultado = await algumaPromessa();
       console.log(resultado);
     } catch (erro) {
       console.error(erro);
     }
   }
   ```

## **Promessas em Sequência:**

   Você pode usar várias chamadas `await` em sequência para realizar operações assíncronas em ordem.

   ```javascript
   async function exemplo() {
     const resultado1 = await promessa1();
     const resultado2 = await promessa2();
     console.log(resultado1, resultado2);
   }
   ```

## **Promessas em Paralelo:**

   Para realizar várias operações assíncronas em paralelo e aguardar que todas sejam concluídas, use `Promise.all`:

   ```javascript
   async function exemplo() {
     const [resultado1, resultado2] = await Promise.all([promessa1(), promessa2()]);
     console.log(resultado1, resultado2);
   }
   ```

## **Funções Anônimas Assíncronas:**

   Você também pode criar funções assíncronas anônimas:

   ```javascript
   const minhaFuncaoAssincrona = async () => {
     // Código assíncrono aqui
   };
   ```

## **Funções de Setas com `async` e `await`:**

   As funções de setas também podem ser assíncronas:

   ```javascript
   const exemplo = async () => {
     const resultado = await algumaPromessa();
     console.log(resultado);
   };
   ```

## **Retorno de Valores:**

   Funções assíncronas sempre retornam promessas. O valor retornado é o valor com o qual a promessa é resolvida.

   ```javascript
   async function exemplo() {
     return 'Olá, Mundo!';
   }
   ```

   Ao chamar `exemplo()`, você obtém uma promessa que será resolvida com o valor `'Olá, Mundo!'`.
