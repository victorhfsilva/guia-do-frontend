# **Renderização no React**

O objetivo principal do React é renderizar eficientemente HTML em uma página da web. O processo de renderização envolve o uso da função `createRoot()` e seu método associado `render()`.

## **A Função createRoot:**
   
   - **Definição:** A função `createRoot()` recebe um elemento HTML como seu único argumento.
   
   - **Propósito:** Ela designa o elemento HTML onde um componente React deve ser apresentado.

## **Método render:**
   
   - **Invocação:** O método `render()` é posteriormente invocado para especificar o componente React que deve ser renderizado.
   
   - **Destino:** O destino da renderização é frequentemente um elemento `<div>` encontrado no arquivo index.html da pasta "public".

## **Exemplo: Configurando um Servidor React.js:**
   
   - **Trecho de Código:**
   
     ```javascript
     const container = document.getElementById('root');
     const root = ReactDOM.createRoot(container);
     root.render(<p>Olá</p>);
     ```
   
   - **Resultado:** O conteúdo renderizado é exibido dentro do elemento `<div id="root">`.

## **Código HTML e JSX:**
  
   - **Uso de JSX:** O código HTML no React é frequentemente expresso usando JSX, que permite tags HTML dentro do código JavaScript.

   - **Exemplo:**
     ```javascript
     const myelement = (
       <table>
         <tr>
           <th>Nome</th>
         </tr>
         <tr>
           <td>John</td>
         </tr>
         <tr>
           <td>Elsa</td>
         </tr>
       </table>
     );

     const container = document.getElementById('root');
     const root = ReactDOM.createRoot(container);
     root.render(myelement);
     ```
   - **Resultado:** A variável JSX é renderizada dentro do nó raiz designado.

## **O Nó Raiz:**
   
   - **Definição:** O nó raiz é o elemento HTML onde o resultado renderizado é exibido.
   
   - **Conceito de Contêiner:** Ele serve como um contêiner para o conteúdo gerenciado pelo React.
   
   - **Flexibilidade:** Não precisa ser um elemento `<div>`, e o id não precisa ser 'root'.

### **Personalizando o Nó Raiz:**
   
   - **Exemplo:**
   
     ```javascript
     <body>
       <header id="sandy"></header>
     </body>
     ```
     ```javascript
     const container = document.getElementById('sandy');
     const root = ReactDOM.createRoot(container);
     root.render(<p>Hallo</p>);
     ```
   
   - **Resultado:** O resultado é exibido dentro do elemento `<header id="sandy">`.
