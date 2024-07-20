# Recoil com React e TypeScript

### Introdução

Recoil é uma biblioteca de gerenciamento de estado para React, desenvolvida pela equipe do Facebook. Ele oferece uma maneira simples e eficiente de gerenciar estados globais e derivados em aplicações React. 

### Configuração do Projeto

#### Inicializando o Projeto

Primeiro, vamos criar um novo projeto React com TypeScript. Execute o comando abaixo no terminal:

```bash
npx create-react-app my-recoil-app --template typescript
```

#### Instalando Recoil

Depois de criar o projeto, navegue até o diretório do projeto e instale o Recoil:

```bash
cd my-recoil-app
npm install recoil
```

### Configurando o Recoil Root

Para usar o Recoil, precisamos configurar o `RecoilRoot` no nível superior da nossa aplicação. Isso geralmente é feito no arquivo `index.tsx` ou `App.tsx`.

#### `index.tsx`

```tsx
import React from 'react';
import ReactDOM from 'react-dom';
import { RecoilRoot } from 'recoil';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <RecoilRoot>
      <App />
    </RecoilRoot>
  </React.StrictMode>,
  document.getElementById('root')
);
```

### Criando Átomos e Selectors

#### Átomos

Átomos são unidades de estado que podem ser lidas ou escritas por qualquer componente. Vamos criar um átomo simples para gerenciar o estado de um contador.

#### `state/counterAtom.ts`

```tsx
import { atom } from 'recoil';

export const counterState = atom<number>({
  key: 'counterState', // unique ID (with respect to other atoms/selectors)
  default: 0, // default value (aka initial value)
});
```

#### Selectors

Selectors são funções assíncronas ou síncronas que transformam o estado. Vamos criar um selector que derive um valor do nosso `counterState`.

#### `state/counterSelector.ts`

```tsx
import { selector } from 'recoil';
import { counterState } from './counterAtom';

export const doubleCounterState = selector<number>({
  key: 'doubleCounterState',
  get: ({ get }) => {
    const count = get(counterState);
    return count * 2;
  },
});
```

### Usando Átomos e Selectors nos Componentes

#### Atualizando o Átomo

Vamos criar um componente que exibe e atualiza o valor do contador.

#### `components/Counter.tsx`

```tsx
import React from 'react';
import { useRecoilState } from 'recoil';
import { counterState } from '../state/counterAtom';

const Counter: React.FC = () => {
  const [count, setCount] = useRecoilState(counterState);

  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
};

export default Counter;
```

Caso deseja criar um componente que só exibe o estado é possível utilizar o hook `useRecoilValue`.

```typescript
import React from 'react';
import { useRecoilValue} from 'recoil';
import { counterState } from '../state/counterAtom';

const Counter: React.FC = () => {
  const count = useRecoilValue(counterState);

  return (
    <div>
      <h1>Counter: {count}</h1>
    </div>
  );
};

export default Counter;
```

Agora, caso deseje criar um componente que apenas atualize o estado é possível utilizar o hook `useSetRecoilState`.

```typescript
import React from 'react';
import { useSetRecoilState } from 'recoil';
import { counterState } from '../state/counterAtom';

const Counter: React.FC = () => {
  const setCount = useSetRecoilState(counterState);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
};

export default Counter;
```

Ainda existem outros hooks como `useResetRecoilState` para resetar o estado para seu valor padrão.

#### Usando um Selector

Agora, vamos criar um componente que exibe o valor derivado (dobrado) do nosso contador.

#### `components/DoubleCounter.tsx`

```tsx
import React from 'react';
import { useRecoilValue } from 'recoil';
import { doubleCounterState } from '../state/counterSelector';

const DoubleCounter: React.FC = () => {
  const doubleCount = useRecoilValue(doubleCounterState);

  return (
    <div>
      <h1>Double Counter: {doubleCount}</h1>
    </div>
  );
};

export default DoubleCounter;
```

### Montando a Aplicação

Finalmente, vamos montar nossa aplicação no componente `App.tsx`.

#### `App.tsx`

```tsx
import React from 'react';
import Counter from './components/Counter';
import DoubleCounter from './components/DoubleCounter';

const App: React.FC = () => {
  return (
    <div>
      <Counter />
      <DoubleCounter />
    </div>
  );
};

export default App;
```
