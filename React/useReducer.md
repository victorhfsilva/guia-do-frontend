# `useReducer`

O `useReducer` é um hook no React que é usado para gerenciar o estado complexo de um componente, especialmente quando esse estado envolve lógica mais avançada, como atualizações condicionais. Aqui está um guia rápido sobre como usar o `useReducer`:

## **Importação:**

   Você precisa importar o `useReducer` do React:

   ```javascript
   import React, { useReducer } from 'react';
   ```

## **Definindo um Reducer:**

   Um reducer é uma função que especifica como o estado do componente deve ser atualizado com base em uma ação. Ele tem a seguinte assinatura:

   ```javascript
   function reducer(state, action) {
     
     switch (action.type) {
       
       case 'TIPO_DA_ACAO':
         return novoEstado;
       
       // Outros casos de ação aqui
       
       default:
         return state;
     }
   }
   ```

## **Criando o Estado Inicial:**

   Antes de usar o `useReducer`, defina o estado inicial do useReducer. 

   ```javascript
   const initialState = {
     propriedade1: 'valor1',
     propriedade2: 'valor2',
     // Mais propriedades iniciais
   };
   ```

## **Inicializando o Reducer:**

   Use o `useReducer` para inicializar o estado e o reducer:

   ```javascript
   const [state, dispatch] = useReducer(reducer, initialState);
   ```

   - `state`: Representa o estado atual.
   - `dispatch`: Uma função que você usará para despachar ações e atualizar o estado.

## **Despachando Ações:**

   Para atualizar o estado, você despacha ações chamando `dispatch` com um objeto de ação:

   ```javascript
   dispatch({ type: 'TIPO_DA_ACAO', payload: dados });
   ```

## **Exemplos de Uso:**

   Aqui estão alguns exemplos de como usar o `useReducer`:

   ```javascript
   import React, { useReducer } from 'react';

   function reducer(state, action) {
     
     switch (action.type) {
     
      case 'INCREMENT':
         return { count: state.count + 1 };
      
      case 'DECREMENT':
         return { count: state.count - 1 };
      
      default:
         return state;
     
     }
   }

   const initialState = { count: 0 };

   function Counter() {
     const [state, dispatch] = useReducer(reducer, initialState);

     return (
       <div>
         <p>Count: {state.count}</p>
         <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
         <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
       </div>
     );
   }

   export default Counter;
   ```

Ou, em tsx:

   ```typescript
    iport { useReducer } from 'react';

    interface ContadorEstado {
        contagem: number
    }

    type AcaoTipo = | {tipo: 'incremento', valor: number} | {tipo: 'decremento'};

    function reducer(estado:ContadorEstado, acao: AcaoTipo) {
        
        switch (acao.tipo) {
            
            case 'incremento':
                return {contagem: estado.contagem + acao.valor};
            
            case 'decremento':
                return {contagem: estado.contagem - 1};
            
            default:
                throw new Error('Ação Inválida');
        }
    }

    export function Contador() {
        
        const estadoInicial: ContadorEstado = {contagem: 0};
        
        const [estado, dispatch] = useReducer(reducer, estadoInicial);

        const handleClickMais = () => {
            dispatch({tipo:'incremento', valor:2});
        };

        const handleClickMenos = () => {
            dispatch({tipo:'decremento'})
        };


        return (
            <>
                <button onClick={handleClickMais}>+</button>
                <button onClick={handleClickMenos}>+</button>
                <span>contagem = {estado.contagem}</span>
            </>
        )
    }
   ```

   Neste exemplo, o estado do contador é gerenciado usando o `useReducer`, e ações 'INCREMENT' e 'DECREMENT' atualizam o estado de acordo.

## **Benefícios do `useReducer`**

   - Útil para gerenciar estados complexos e atualizações condicionais.
   - Ajuda a manter a lógica de atualização de estado separada do componente.
