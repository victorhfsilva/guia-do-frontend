# Web Storage em JavaScript

O Web Storage em JavaScript oferece duas opções principais: `localStorage` e `sessionStorage`. Ambos fornecem uma maneira de armazenar dados no lado do cliente, mas diferem em termos de persistência, escopo e limites de armazenamento.

## **`localStorage`:**

1. **Persistência de Dados:**
   - Os dados persistem além da sessão do navegador.

2. **Escopo de Acesso:**
   - Compartilhado entre todas as abas ou janelas abertas no mesmo domínio.

3. **Limite de Armazenamento:**
   - Geralmente em torno de 5 MB.

4. **Exemplo:**
   ```javascript
   // Armazenar dados em localStorage
   localStorage.setItem('nome', 'Alice');

   // Recuperar dados de localStorage
   const nome = localStorage.getItem('nome');
   console.log(nome); // Saída: Alice
   ```

## **`sessionStorage`:**

1. **Persistência de Dados:**
   - Os dados são descartados quando a sessão do navegador é encerrada.

2. **Escopo de Acesso:**
   - Restrito à aba ou janela específica que os criou.

3. **Limite de Armazenamento:**
   - Geralmente em torno de 5 MB.

4. **Exemplo:**
   ```javascript
   // Armazenar dados em sessionStorage
   sessionStorage.setItem('cidade', 'Paris');

   // Recuperar dados de sessionStorage
   const cidade = sessionStorage.getItem('cidade');
   console.log(cidade); // Saída: Paris
   ```

## **Quando Usar:**

- **`localStorage`:**
  - Para armazenar dados persistentes compartilhados entre abas ou janelas.

- **`sessionStorage`:**
  - Para dados temporários válidos apenas durante a sessão e acessíveis localmente.

Lembre-se de escolher o tipo de Web Storage com base na necessidade específica do seu aplicativo, considerando a persistência, o escopo e os limites de armazenamento.