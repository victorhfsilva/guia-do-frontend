# `useRef`

## Introdução ao useRef

O `useRef` é um hook do React que permite referenciar valores no DOM ou persistir valores entre renderizações. Ele é útil para armazenar valores mutáveis que não causam uma nova renderização quando atualizados.

### Sintaxe Básica

```jsx
import { useRef } from 'react';

const ref = useRef(initialValue);
```

- `initialValue`: Valor inicial do ref. Se não fornecido, o valor inicial é `null`.

### Retorno

- `ref`: Objeto que contém a propriedade `current`.
  - `ref.current`: Retorna o valor atual do ref.
  - `ref.current = value`: Define o valor do ref.

## Usos Comuns

### Acesso Direto a Elementos DOM

```jsx
import { useRef } from 'react';

const App = () => {
  const inputRef = useRef();

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input type="text" ref={inputRef} />
      <button onClick={focusInput}>Focar Input</button>
    </>
  );
};
```

Neste exemplo, `inputRef` é usado para acessar diretamente o elemento de input no DOM.

### Contagem de Renderizações

```jsx
import { useState, useEffect, useRef } from 'react';

const App = () => {
  const [inputValue, setInputValue] = useState('');
  const renderCount = useRef(0);

  useEffect(() => {
    renderCount.current = renderCount.current + 1;
  });

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h1>Contagem de Renderizações: {renderCount.current}</h1>
    </>
  );
};
```

Neste exemplo, `renderCount` é usado para rastrear a contagem de renderizações sem causar uma re-renderização.

### Rastreamento de Mudanças de Estado

```jsx
import { useState, useEffect, useRef } from 'react';

const App = () => {
  const [inputValue, setInputValue] = useState('');
  const prevInputValue = useRef('');

  useEffect(() => {
    prevInputValue.current = inputValue;
  }, [inputValue]);

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h2>Valor Atual: {inputValue}</h2>
      <h2>Valor Anterior: {prevInputValue.current}</h2>
    </>
  );
};
```

Neste exemplo, `prevInputValue` é usado para manter o controle dos valores anteriores do estado `inputValue`.

### Outros Usos

O `useRef` também pode ser usado para manter referências a propriedades de componentes ou valores arbitrários.

```jsx
import { useState, useRef } from 'react';

// Exemplo 1
const App1 = () => {
  const [count, setCount] = useState(0);
  const countRef = useRef(count);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Aumentar</button>
      <p>Contagem: {countRef.current}</p>
    </div>
  );
};

// Exemplo 2
const App2 = () => {
  const customRef = useRef('Olá, mundo!');

  return (
    <div>
      <p>{customRef.current}</p>
      <button onClick={() => customRef.current = 'Adeus, mundo!'}>Alterar</button>
    </div>
  );
};
```

Nos exemplos acima, `countRef` é usado para manter uma referência à propriedade `count` e `customRef` é usado para manter uma referência a uma string arbitrária.

**Observação:** `useRef` é uma ferramenta versátil no React, útil para diversos cenários, desde acesso a elementos DOM até rastreamento de valores entre renderizações.