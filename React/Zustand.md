# Zustand no React

O Zustand é uma biblioteca de gerenciamento de estado para o React que proporciona uma maneira simples e eficiente de lidar com o estado da aplicação. 

## Configuração Inicial

Antes de começar, é necessário instalar o Zustand e suas dependências. Utilize o seguinte comando:

```bash
npm install zustand immer
```

## Criando um Store

Para criar um store no Zustand, você pode usar a função `create` fornecida pela biblioteca. Aqui está um exemplo de como criar um store para um contador:

```tsx
import create from 'zustand';

type CounterState = {
  count: number;
  increment: () => void;
  decrement: () => void;
};

const useCounterStore = create<CounterState>((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));
```

## Hooks Personalizados

Para utilizar o estado dentro de um componente, você pode criar um hook personalizado como o `useCounterStore` do exemplo acima. Este hook fornece acesso ao estado e às funções de atualização do store.

```tsx
import { useCounterStore } from './caminho/do/seu/store';

const MeuComponente: React.FC = () => {
  const { count, increment, decrement } = useCounterStore();

  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={increment}>Incrementar</button>
      <button onClick={decrement}>Decrementar</button>
    </div>
  );
};
```

### Tipagem do Estado

Ao utilizar o TypeScript, é crucial definir as interfaces para o estado do seu store. Isso proporciona uma melhor autocompreensão do código e ajuda na detecção de erros.

```tsx
interface CounterState {
  count: number;
  increment: () => void;
  decrement: () => void;
}

const useCounterStore = create<CounterState>((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));
```