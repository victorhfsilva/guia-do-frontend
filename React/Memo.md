# React.memo

### Introdução

`React.memo` é uma função de ordem superior do React que pode ser usada para otimizar componentes funcionais. Ele memoriza o resultado de renderizações anteriores e evita renderizações desnecessárias ao comparar as novas props com as antigas. Se as props não mudaram, o componente não é re-renderizado.

## Usando `React.memo`

### Exemplo Básico

Vamos criar um componente simples que será memorizado usando `React.memo`.

#### `components/Child.tsx`

```tsx
import React from 'react';

interface ChildProps {
  name: string;
}

const Child: React.FC<ChildProps> = ({ name }) => {
  console.log('Rendering Child component');
  return <div>Hello, {name}!</div>;
};

export default React.memo(Child);
```

#### `components/Parent.tsx`

```tsx
import React, { useState } from 'react';
import Child from './Child';

const Parent: React.FC = () => {
  const [count, setCount] = useState(0);
  const [name, setName] = useState('John');

  return (
    <div>
      <h1>Parent Component</h1>
      <button onClick={() => setCount(count + 1)}>Increment Count: {count}</button>
      <button onClick={() => setName(name === 'John' ? 'Doe' : 'John')}>Toggle Name</button>
      <Child name={name} />
    </div>
  );
};

export default Parent;
```

### Quando Usar `React.memo`

1. **Componentes Funcionais Puros**: Use `React.memo` para componentes funcionais puros que dependem apenas de suas props e não têm estado interno ou efeitos colaterais.

2. **Componentes que Re-renderizam Frequentemente**: Se um componente está sendo renderizado frequentemente sem necessidade, `React.memo` pode ajudar a otimizar o desempenho.

3. **Componentes com Props Estáveis**: Quando as props passadas para o componente mudam raramente, `React.memo` pode evitar renderizações desnecessárias.

#### Exemplo de Uso Apropriado

Imagine um componente de lista de itens onde cada item é renderizado como um componente separado. Se os itens não mudarem frequentemente, podemos usar `React.memo` para memorizar cada item individualmente.

#### `components/Item.tsx`

```tsx
import React from 'react';

interface ItemProps {
  value: string;
}

const Item: React.FC<ItemProps> = ({ value }) => {
  console.log(`Rendering Item: ${value}`);
  return <div>{value}</div>;
};

export default React.memo(Item);
```

#### `components/ItemList.tsx`

```tsx
import React from 'react';
import Item from './Item';

interface ItemListProps {
  items: string[];
}

const ItemList: React.FC<ItemListProps> = ({ items }) => {
  return (
    <div>
      {items.map(item => (
        <Item key={item} value={item} />
      ))}
    </div>
  );
};

export default ItemList;
```

### Quando Não Usar `React.memo`

1. **Componentes com Props Dinâmicas**: Se as props mudam frequentemente e essas mudanças são necessárias para a renderização correta, `React.memo` pode não trazer benefícios.

2. **Componentes com Estado Interno**: Componentes que gerenciam seu próprio estado ou têm efeitos colaterais complexos podem não se beneficiar de `React.memo`.

3. **Componentes Simples e Leves**: Para componentes muito simples e leves, o custo adicional de verificação de igualdade de props pode não justificar o uso de `React.memo`.

#### Exemplo de Uso Inapropriado

Imagine um componente que atualiza sua exibição baseada em um temporizador interno. Nesse caso, `React.memo` não seria útil, pois o estado interno está sempre mudando.

#### `components/Timer.tsx`

```tsx
import React, { useState, useEffect } from 'react';

const Timer: React.FC = () => {
  const [time, setTime] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setTime(prevTime => prevTime + 1);
    }, 1000);

    return () => clearInterval(interval);
  }, []);

  return <div>Timer: {time}</div>;
};

export default Timer;
```

### Funções de Conciliação Personalizadas 


Por padrão, `React.memo` faz uma comparação rasa (shallow comparison) das props para decidir se o componente deve ser re-renderizado. Em alguns casos, isso pode não ser suficiente, especialmente se as props forem objetos ou arrays complexos que podem ser considerados iguais mesmo se referindo a diferentes instâncias na memória.

Uma função de conciliação personalizada permite que você defina como as props devem ser comparadas. Isso é útil quando você precisa de uma lógica de comparação mais complexa.

#### Sintaxe Básica

A função de conciliação personalizada é passada como o segundo argumento para `React.memo`.

```tsx
const MyComponent = React.memo(Component, (prevProps, nextProps) => {
  // lógica de comparação
  return boolean;
});
```

- `prevProps`: As props anteriores do componente.
- `nextProps`: As novas props do componente.
- Retorne `true` se as props forem consideradas iguais (não re-renderize), e `false` se forem diferentes (re-renderize).

#### Exemplo de Uso

Vamos criar um exemplo onde usamos uma função de conciliação personalizada para comparar arrays de objetos.

#### `components/UserList.tsx`

```tsx
import React from 'react';

interface User {
  id: number;
  name: string;
}

interface UserListProps {
  users: User[];
}

const UserList: React.FC<UserListProps> = ({ users }) => {
  console.log('Rendering UserList');
  return (
    <div>
      {users.map(user => (
        <div key={user.id}>{user.name}</div>
      ))}
    </div>
  );
};

const areEqual = (prevProps: UserListProps, nextProps: UserListProps) => {
  // Comparação profunda das listas de usuários
  if (prevProps.users.length !== nextProps.users.length) {
    return false;
  }
  for (let i = 0; i < prevProps.users.length; i++) {
    if (prevProps.users[i].id !== nextProps.users[i].id || prevProps.users[i].name !== nextProps.users[i].name) {
      return false;
    }
  }
  return true;
};

export default React.memo(UserList, areEqual);
```

#### `components/Parent.tsx`

```tsx
import React, { useState } from 'react';
import UserList from './UserList';

const Parent: React.FC = () => {
  const [users, setUsers] = useState([
    { id: 1, name: 'John' },
    { id: 2, name: 'Doe' }
  ]);

  const addUser = () => {
    setUsers([...users, { id: users.length + 1, name: `User ${users.length + 1}` }]);
  };

  return (
    <div>
      <button onClick={addUser}>Add User</button>
      <UserList users={users} />
    </div>
  );
};

export default Parent;
```

#### Quando Usar Funções de Conciliação Personalizadas

1. **Props Complexas**: Quando as props são objetos complexos, arrays ou outros tipos de dados que exigem uma comparação profunda.
2. **Desempenho**: Para evitar renderizações desnecessárias que possam ocorrer devido a referências diferentes, mas valores iguais.
3. **Otimização de Componentes**: Quando você sabe que a comparação padrão não é suficiente para otimizar o desempenho do componente.

#### Quando Não Usar Funções de Conciliação Personalizadas

1. **Overhead de Desempenho**: Se a função de conciliação personalizada for muito complexa, ela pode introduzir um overhead de desempenho, especialmente se a comparação envolver muitas operações pesadas.
2. **Componentes Simples**: Para componentes simples onde a comparação rasa é suficiente.
3. **Estados de Curta Duração**: Quando o estado do componente muda rapidamente e frequentemente, a otimização pode não ser perceptível.

### Conclusão

`React.memo` é uma ferramenta poderosa para otimizar componentes funcionais em React, mas deve ser usada com discernimento. Ele é mais eficaz em componentes puros, frequentemente renderizados, e com props estáveis. Evite seu uso em componentes com estado interno complexo ou com props que mudam frequentemente.