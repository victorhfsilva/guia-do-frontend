# **JSX em React:**

## **O que é JSX?**
   - **Definição:** JSX significa JavaScript XML.
   - **Função:** Permite escrever HTML dentro do React, facilitando a construção de interfaces.

## **Códigos JSX:**
   - Permite escrever elementos HTML diretamente em JavaScript, eliminando a necessidade de `createElement()` e/ou `appendChild()`.
   
   - Transforma tags HTML em elementos React.
   
   - **Exemplo 1 - Com JSX:**
     ```jsx
     const meuElemento = <h1>Eu amo JSX!</h1>;

     const raiz = ReactDOM.createRoot(document.getElementById('root'));
     raiz.render(meuElemento);
     ```

   - **Exemplo 2 - Sem JSX:**
     ```jsx
     const meuElemento = React.createElement('h1', {}, 'Eu não uso JSX!');

     const raiz = ReactDOM.createRoot(document.getElementById('root'));
     raiz.render(meuElemento);
     ```

## **Expressões em JSX:**
   - Expressões javascript podem ser escritas entre chaves `{ }` em JSX.
   
   - **Exemplo:**
     ```jsx
     const meuElemento = <h1>React é {5 + 5} vezes melhor com JSX</h1>;
     ```

## **Formatação de Blocos HTML:**
   - Para escrever HTML em várias linhas, coloque o HTML entre parênteses.
   
   - **Exemplo:**
     ```jsx
     const meuElemento = (
       <ul>
         <li>Maçãs</li>
         <li>Bananas</li>
         <li>Cerejas</li>
       </ul>
     );
     ```

  - O código HTML também precisa ser envolvido em UM único elemento de nível superior.

   - **Exemplo:**
     ```jsx
     const meuElemento = (
       <div>
         <p>Eu sou um parágrafo.</p>
         <p>Eu sou outro parágrafo.</p>
       </div>
     );
     ```
   - Alternativamente, pode-se utilizar um "fragmento" para evitar adicionar nós extras ao DOM.
     ```jsx
     const meuElemento = (
       <>
         <p>Eu sou um parágrafo.</p>
         <p>Eu sou outro parágrafo.</p>
       </>
     );
     ```


## **Atributo  `className`:**
   - O uso de `class` como atributo é proibido devido à reserva em JavaScript, por isso usa-se `className` em vez de `class`.
   - **Exemplo:**
     ```jsx
     const meuElemento = <h1 className="minhaClasse">Olá Mundo</h1>;
     ```
