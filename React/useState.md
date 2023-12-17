# useState

## Importação

```javascript
import React, { useState } from 'react';
```

## Declaração de um Estado

```javascript
const [state, setState] = useState(initialValue);
```

- `state`: A variável que armazena o estado.
- `setState`: A função usada para atualizar o estado.
- `initialValue`: O valor inicial do estado.

## Uso Básico

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```
## Uso com Styled-Components

```javascript
import styled from 'styled-components';

const Button = styled.button`
  background-color: ${(props) => (props.primary ? 'blue' : 'gray')};
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
`;

function App() {
  const [isPrimary, setIsPrimary] = useState(false);

  const toggleStyle = () => {
    setIsPrimary(!isPrimary);
  };

  return (
    <div>
      <Button primary={isPrimary} onClick={toggleStyle}>
        Toggle Style
      </Button>
    </div>
  );
}
```

## Uso com Componentes Controlados

```javascript
function InputField() {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  return (
    <input
      type="text"
      value={inputValue}
      onChange={handleChange}
      placeholder="Type something..."
    />
  );
}
```

Ou, em tsx: 

```typescript
function InputField() {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (event: React.ChangeEvent<HTMLInputElement>) => {
    setInputValue(event.target.value);
  };

  return (
    <input
      value={inputValue}
      onChange={handleChange}
    />
    <p>O input inserido é {inputValue}</p>
  );
}
```

## Definindo o tipo do estado no Typescript

- O tipo do estado pode ser definido por inferência:

```typescript
const [state, setState] = useState(false);
// `state` is inferred to be a boolean
// `setState` only takes booleans
```

- Caso um estado seja inicializado como nulo, podemos definir o tipo como nos exemplos a seguir:

```typescript
//Declarando explicitamente o tipo
const [user, setUser] = useState<User | null>(null);

// later
setUser(newUser);
```

```typescript
//Usando asserção de tipos
const [user, setUser] = useState<User>({} as User);

// later
setUser(newUser);
```
