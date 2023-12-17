# `useCallback`

O hook `useCallback` é usado para memorizar funções em componentes funcionais do React, especialmente aquelas que são passadas como propriedades para componentes filhos. Ele ajuda a otimizar o desempenho, garantindo que funções não sejam recriadas a cada renderização, a menos que as dependências especificadas mudem.

```javascript
import { useCallback } from 'react';

const memorizedCallback = useCallback(
  () => {
    // Lógica da função
  },
  [dependency1, dependency2]
);
```

## Uso Básico

- `useCallback` recebe uma função e um array de dependências como argumentos.
- A função passada para `useCallback` é a função que você deseja memorizar.
- O array de dependências contém variáveis que, quando alteradas, acionarão a recriação da função memorizada.

## Exemplo de Uso

```javascript
import { useCallback, useState } from 'react';

function ParentComponent() {
  const [count, setCount] = useState(0);

  // Use useCallback para memorizar a função handleIncrement.
  const handleIncrement = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <ChildComponent onIncrement={handleIncrement} />
    </div>
  );
}

function ChildComponent({ onIncrement }) {
  return (
    <button onClick={onIncrement}>Increment</button>
  );
}
```

Neste exemplo, a função `handleIncrement` é memorizada usando `useCallback`, garantindo que ela não seja recriada a cada renderização do componente pai.

## Dica de Uso

- Use `useCallback` quando precisar passar funções como props para componentes filhos para evitar recriações desnecessárias.
- Evite utilizar `useCallback` em todas as funções do seu componente, apenas naquelas que têm dependências que precisam ser rastreadas.
- Lembre-se de que, embora `useCallback` seja útil para otimização de desempenho, não é necessário em todos os casos. Use-o quando houver um motivo real para evitar recriações de funções.
