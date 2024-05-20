# React Query

## O que é o React Query?

O React Query é uma biblioteca para gerenciamento de estado de dados assíncronos em aplicações React. Ele facilita o fetching, caching, sincronização e atualização de dados de maneira simples e eficiente.

## Instalação

Para começar a usar o React Query, você precisa instalá-lo no seu projeto:

```bash
npm install @tanstack/react-query
```

## Configuração Inicial

Você precisa configurar o `QueryClient` e o `QueryClientProvider` no nível mais alto do seu aplicativo, geralmente no componente raiz:

```jsx
import React from 'react';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import App from './App';

const queryClient = new QueryClient();

function Root() {
  return (
    <QueryClientProvider client={queryClient}>
      <App />
    </QueryClientProvider>
  );
}

export default Root;
```

## Uso Básico

Aqui está um exemplo básico de como usar o React Query para buscar dados de uma API:

```jsx
import React from 'react';
import { useQuery } from '@tanstack/react-query';

const fetchUsers = async () => {
  const res = await fetch('https://jsonplaceholder.typicode.com/users');
  return res.json();
};

function Users() {
  const { data, error, isLoading } = useQuery(['users'], fetchUsers);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;

  return (
    <ul>
      {data.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}

export default Users;
```

### Explicação do Código

1. **fetchUsers**: Uma função assíncrona que busca os dados da API.
2. **useQuery**: Um hook que aceita uma chave única (['users']) e uma função de fetching (fetchUsers). Ele retorna o estado da consulta (`data`, `error`, `isLoading`).

## Parâmetros de Configuração

Você pode configurar vários parâmetros para o `useQuery`:

```jsx
const { data, error, isLoading } = useQuery(['users'], fetchUsers, {
  staleTime: 5000, // Tempo até os dados serem considerados "stale" (em milissegundos)
  cacheTime: 10000, // Tempo que os dados permanecem no cache após ficarem "stale"
  refetchOnWindowFocus: true, // Refetch ao focar na janela
});
```

## Mutations

O React Query também lida com operações de escrita, como POST, PUT, DELETE, através do hook `useMutation`:

```jsx
import React from 'react';
import { useMutation, useQueryClient } from '@tanstack/react-query';

const addUser = async (newUser) => {
  const res = await fetch('https://jsonplaceholder.typicode.com/users', {
    method: 'POST',
    body: JSON.stringify(newUser),
    headers: {
      'Content-Type': 'application/json',
    },
  });
  return res.json();
};

function AddUser() {
  const queryClient = useQueryClient();
  const mutation = useMutation(addUser, {
    onSuccess: () => {
      // Invalidate and refetch
      queryClient.invalidateQueries(['users']);
    },
  });

  const handleSubmit = () => {
    mutation.mutate({ name: 'New User' });
  };

  return (
    <div>
      <button onClick={handleSubmit}>Add User</button>
      {mutation.isLoading && <p>Adding user...</p>}
      {mutation.isError && <p>Error adding user: {mutation.error.message}</p>}
      {mutation.isSuccess && <p>User added!</p>}
    </div>
  );
}

export default AddUser;
```

## Ferramentas e DevTools

O React Query vem com DevTools que podem ser integrados na sua aplicação para facilitar o desenvolvimento e debug:

```bash
npm install @tanstack/react-query-devtools
```

```jsx
import { ReactQueryDevtools } from '@tanstack/react-query-devtools';

// Dentro do QueryClientProvider
<QueryClientProvider client={queryClient}>
  <App />
  <ReactQueryDevtools initialIsOpen={false} />
</QueryClientProvider>
```

## Conclusão

O React Query é uma ferramenta poderosa para gerenciamento de dados assíncronos em aplicações React. Ele simplifica o fetching, caching, sincronização e atualização de dados, proporcionando uma experiência de desenvolvimento mais eficiente e performática. 

Para mais informações e exemplos avançados, consulte a [documentação oficial do React Query](https://react-query.tanstack.com/).