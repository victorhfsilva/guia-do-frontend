# `useMemo`

O hook `useMemo` é usado para memorizar o resultado de uma função ou cálculo complexo para evitar cálculos desnecessários sempre que um componente for renderizado. Ele é útil para otimizar o desempenho de um componente, garantindo que valores calculados sejam reutilizados, a menos que as dependências especificadas mudem.

```javascript
import { useMemo } from 'react';

const memoizedValue = useMemo(() => {
  // Cálculos ou lógica complexa
  return computedValue;
}, [dependency1, dependency2]);
```

## Uso Básico

- `useMemo` recebe uma função e um array de dependências como argumentos.
- A função passada para `useMemo` contém a lógica que você deseja memorizar.
- O array de dependências contém variáveis que, quando alteradas, acionarão o recálculo do valor memorizado.

## Exemplo de Uso

```javascript
import { useMemo, useState } from 'react';

function Component() {
  const [count, setCount] = useState(0);

  // Use useMemo para calcular o quadrado de 'count' apenas quando 'count' mudar.
  const squared = useMemo(() => {
    console.log('Calculating squared value');
    return count * count;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Squared: {squared}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

Neste exemplo, o valor de `squared` só será recalculado quando `count` mudar.

## Dica de Uso

- Use `useMemo` para evitar cálculos caros ou chamadas de função que não precisam ser refeitas a cada renderização.
- Evite utilizar `useMemo` em excesso, pois pode aumentar a complexidade do código e impactar negativamente o desempenho se usado indiscriminadamente.

**Lembre-se**: Use `useMemo` quando tiver certeza de que os cálculos são custosos e devem ser evitados em renderizações desnecessárias. 