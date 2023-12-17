# **Diferença entre Formulários Controlados e Não Controlados**

Formulários controlados e não controlados são duas abordagens diferentes para lidar com dados de formulários no React. Cada abordagem tem suas próprias características e casos de uso. Vamos explorar as diferenças entre essas duas técnicas.

## Formulários Controlados:

1. **Definição de Estado:**
   - Em formulários controlados, os elementos do formulário (como inputs) são vinculados ao estado do React.
   - O estado é mantido no componente React e serve como fonte única de verdade para os valores dos campos do formulário.

2. **Atualização através de Eventos:**
   - As mudanças nos campos do formulário são gerenciadas por manipuladores de eventos, geralmente a função `onChange`.
   - Cada vez que um usuário digita algo, o estado é atualizado, e o componente é re-renderizado com os novos valores.

3. **Acesso aos Dados:**
   - Os dados do formulário podem ser acessados diretamente a partir do estado do componente.

4. **Validação Facilitada:**
   - A validação de campos e a manipulação de erros são mais fáceis, pois você tem controle total sobre os dados e pode aplicar lógica de validação no momento da atualização do estado.

5. **Exemplo de Código:**
   ```jsx
   import React, { useState } from 'react';

   const ControlledForm = () => {
     const [inputValue, setInputValue] = useState('');

     const handleChange = (e) => {
       setInputValue(e.target.value);
     };

     return (
       <form>
         <input type="text" value={inputValue} onChange={handleChange} />
       </form>
     );
   };
   ```

## Formulários Não Controlados:

1. **Uso de Refs:**
   - Em formulários não controlados, os elementos do formulário não estão vinculados ao estado do React.
   - Em vez disso, você utiliza refs para acessar os valores dos campos diretamente a partir do DOM.

2. **Atualização Direta no DOM:**
   - As mudanças nos campos do formulário não são refletidas no estado do React. Em vez disso, você atualiza diretamente o DOM usando refs.

3. **Acesso aos Dados:**
   - Os dados do formulário podem ser acessados lendo os valores diretamente dos elementos do DOM usando refs.

4. **Validação Pode ser Mais Complexa:**
   - Como os dados não são armazenados no estado do React, a validação pode ser mais complexa, e você precisa lidar diretamente com a lógica de validação no momento da submissão.

5. **Exemplo de Código:**
   ```jsx
   import React, { useRef } from 'react';

   const UncontrolledForm = () => {
     const inputRef = useRef();

     const handleSubmit = (e) => {
       e.preventDefault();
       console.log('Input Value:', inputRef.current.value);
     };

     return (
       <form onSubmit={handleSubmit}>
         <input type="text" ref={inputRef} />
         <button type="submit">Submit</button>
       </form>
     );
   };
   ```

## Escolha entre Controlado e Não Controlado:

- **Formulários Controlados são Ideais:**
  - Para formulários simples a moderadamente complexos.
  - Quando você precisa de validação e manipulação de dados mais fácil.

- **Formulários Não Controlados Podem Ser Úteis:**
  - Em situações específicas, como formulários muito grandes ou quando a manipulação direta do DOM é necessária.
  - Em integrações com bibliotecas externas que gerenciam seu próprio estado interno.

Em geral, a escolha entre formulários controlados e não controlados depende da complexidade do seu formulário e dos requisitos específicos do seu aplicativo. Formulários controlados oferecem um controle mais robusto, enquanto formulários não controlados podem ser mais simples em situações específicas.