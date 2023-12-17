# `useEffect` 

## O que é o `useEffect`?

O `useEffect` é um hook do React que permite que você realize efeitos colaterais em componentes funcionais. Ele é usado para lidar com operações que não se encaixam na renderização principal, como chamadas de API, manipulação do DOM e gerenciamento de assinaturas.

## Importando o `useEffect`

```jsx
import React, { useEffect } from 'react';
```

## Sintaxe básica do `useEffect`

```jsx
useEffect(() => {
  // Código para executar o efeito
}, [dependencias]);
```

- O primeiro argumento é uma função que contém o código do efeito.
- O segundo argumento é uma matriz de dependências (opcional). O efeito será reexecutado se alguma das dependências mudar. Se omitido, o efeito será executado após cada renderização.

## Exemplo de uso básico

```jsx
useEffect(() => {
  console.log('O componente foi montado.');
  return () => {
    console.log('O componente foi desmontado.');
  };
}, []);
```

- Neste exemplo, o código dentro do `useEffect` é executado quando o componente é montado e também é executado quando o componente é desmontado.

## Executando o efeito após renderização

```jsx
useEffect(() => {
  // Código para executar após cada renderização
});
```

- Quando o segundo argumento é omitido, o efeito é executado após cada renderização do componente.

## Executando o efeito apenas na primeira renderização

```jsx
useEffect(() => {
  // Código para executar apenas na primeira renderização
}, []);
```

- Passar uma matriz vazia como segundo argumento faz com que o efeito seja executado apenas uma vez, na primeira renderização do componente.

## Executando o efeito quando as dependências mudam

```jsx
const [count, setCount] = useState(0);

useEffect(() => {
  console.log(`O valor de count é: ${count}`);
}, [count]);
```

- O efeito será executado na primeira renderização e sempre que o valor de `count` mudar.

## Limpando o efeito

```jsx
useEffect(() => {
  // Código do efeito
  return () => {
    // Código de limpeza (opcional)
  };
}, [dependencias]);
```

- Você pode retornar uma função de limpeza que será executada quando o componente for desmontado ou quando as dependências mudarem.

### Exemplos


#### Exemplo 1:

```javascript
import React, { useState, useEffect } from 'react';

function ExampleComponent() {
  const [count, setCount] = useState(0);

  // useEffect para atualizar o título da página quando 'count' muda
  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

Neste exemplo, o `useEffect` é usado para atualizar o título da página toda vez que o estado `count` muda.

### Exemplo 2:

```javascript
import React, { useState, useEffect } from 'react';

function UseStateExample() {
  const [message, setMessage] = useState('');

  // useEffect para definir uma mensagem após um atraso
  useEffect(() => {
    const timer = setTimeout(() => {
      setMessage('Olá, Mundo!');
    }, 2000);

    return () => {
      clearTimeout(timer);
    };
  }, []);

  return (
    <div>
      <p>{message}</p>
    </div>
  );
}
```

### Exemplo 3

```typescript
import { useState, useEffect } from 'react';

export function Relogio() {
  const [horario, setHorario] = useState(new Date());
  
  useEffect(() => {

    function tick() {
      setHorario(new Date());
    }

    const temporizador = setInterval(() => tick(), 1000);

    return () => {
      clearInterval(temporizador);
    }
    
  }, [] );

  return (
    <>
      <h1>Relógio:</h1>
      <h2>{horario.toLocaleTimeString()}</h2>
    </>
  )
}
```