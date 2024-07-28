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
  const { data, error, isLoading } = useQuery({ queryKey: ['users'], queryFn: fetchUsers });

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

Ou, usando axios e typescript:

```typescript
const api = axios.create({
    baseURL: "https://viacep.com.br/ws"
});

const getCep = (cep: string): Promise<AddressType> => {
    return api.get<AddressType>(`/${cep}/json`).then((response) => {
        return response.data;
    })
}

const Cep = () => {
    const { cep } = useParams<string>()

    const { data, error, isLoading } = useQuery<AddressType, AxiosError>({
        queryKey: ['cep', cep],
        queryFn: () => getCep(cep || "")
    })

    if (isLoading) return (
        <div className="address-div">
            <ThreeDot color="#888" size="medium" text="" textColor="" />
        </div>
    )

    if (error) return <div className="address-div">Error: {error.message}</div>;

    if (data?.cep === undefined) {
        return <div className="address-div">Cep not found.</div>
    }

    return (
        <div className="address-div">
            <h3>CEP</h3>
            <div className="address-data-div">
                <p>CEP: {data?.cep}</p>
                <p>Address: {data?.logradouro}</p>
                <p>Complemento: {data?.complemento}</p>
                <p>Bairro: {data?.bairro}</p>
                <p>Localidade: {data?.localidade}</p>
                <p>UF: {data?.uf}</p>
            </div>
        </div>
    )

}
```


### Explicação do Código

1. **fetchUsers**: Uma função assíncrona que busca os dados da API.
2. **useQuery**: Um hook que aceita uma chave única (`queryKey: ['users']`) e uma função de fetching (`queryFn: fetchUsers`). Ele retorna o estado da consulta (`data`, `error`, `isLoading`).

## Parâmetros de Configuração

Você pode configurar vários parâmetros para o `useQuery`:

```jsx
const { data, error, isLoading } = useQuery({
  queryKey: ['users'],
  queryFn: fetchUsers,
  staleTime: 5000, // Tempo até os dados serem considerados "stale" (em milissegundos)
  cacheTime: 10000, // Tempo que os dados permanecem no cache após ficarem "stale"
  refetchOnWindowFocus: true, // Refetch ao focar na janela
});
```

## Incluindo o Array de Dependências

O useQuery também permite que você defina um array de dependências, semelhante ao hook useEffect do React. Isso pode ser útil quando sua consulta depende de variáveis dinâmicas que podem mudar durante o ciclo de vida do componente. O exemplo a seguir declara uma dependência com userId.

```jsx
const { data, error, isLoading } = useQuery({
  queryKey: ['users', userId],
  queryFn: fetchUsers,
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

## Incluindo o Array de Dependências

O useQuery também permite que você defina um array de dependências, semelhante ao hook useEffect do React. Isso pode ser útil quando sua consulta depende de variáveis dinâmicas que podem mudar durante o ciclo de vida do componente. O exemplo a seguir declara uma dependência com userId.

```jsx
const { data, error, isLoading } = useQuery(['users', userId], fetchUsers, {
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