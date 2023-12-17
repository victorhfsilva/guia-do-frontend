# Contextos no React

## Introdução

O Contexto no React é uma ferramenta que facilita o compartilhamento de dados entre componentes sem a necessidade de passar propriedades manualmente através de cada nível da árvore de componentes. 

## Criando um Contexto

### Criar um Arquivo para o Contexto

Crie um arquivo para o contexto, por exemplo, `MyContext.tsx`:

```jsx
// MyContext.jsx
import React, { createContext, useContext, useState } from 'react';

const MyContext = createContext();

const MyContextProvider = ({ children }) => {
  
  const [data, setData] = useState('');

  const updateData = (newData) => {
    setData(newData);
  };

  return (
    <MyContext.Provider value={{ data, updateData }}>
      {children}
    </MyContext.Provider>
  );
};

const useMyContext = () => {

  const context = useContext(MyContext);
  
  if (!context) {
    throw new Error('useMyContext must be used within a MyContextProvider');
  }
  return context;
};

export { MyContextProvider, useMyContext };
```

Ou, em tsx:

```tsx
// MyContext.tsx
import { createContext, useContext } from 'react';

interface MyContextProps {
  // Defina as propriedades do contexto aqui
  data: string;
  updateData: (newData: string) => void;
}

const MyContext = createContext<MyContextProps | undefined>(undefined);

export const MyContextProvider: React.FC = ({ children }) => {
  // Defina o estado e funções relacionadas ao contexto aqui
  const [data, setData] = React.useState<string>('');

  const updateData = (newData: string) => {
    setData(newData);
  };

  return (
    <MyContext.Provider value={{ data, updateData }}>
      {children}
    </MyContext.Provider>
  );
};

export const useMyContext = (): MyContextProps => {
  const context = useContext(MyContext);
  if (!context) {
    throw new Error('useMyContext deve ser usado dentro de um MyContextProvider');
  }
  return context;
};
```


## Utilizar o Contexto em Componentes

```tsx
// SeuComponente.tsx
import React from 'react';
import { useMyContext } from './MyContext';

const SeuComponente: React.FC = () => {
  const { data, updateData } = useMyContext();

  return (
    <div>
      <p>Dados do Contexto: {data}</p>
      <button onClick={() => updateData('Novos Dados')}>Atualizar Dados</button>
    </div>
  );
};
```

## Envolver a Aplicação no Contexto

No componente que engloba a aplicação, envolva-a com o `MyContextProvider`:

```tsx
// SeuApp.tsx
import React from 'react';
import { MyContextProvider } from './MyContext';
import SeuComponente from './SeuComponente';

const SeuApp: React.FC = () => {
  return (
    <MyContextProvider>
      <SeuComponente />
    </MyContextProvider>
  );
};

export default SeuApp;
```

## Considerações Finais

- Certifique-se de fornecer interfaces claras para os dados no contexto para facilitar a manutenção e compreensão do código.
- Sempre envolva sua aplicação com o provedor do contexto para tornar os dados disponíveis em toda a árvore de componentes.
- Utilize o TypeScript para adicionar tipagem estática e melhorar a segurança do seu código.