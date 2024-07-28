# Interceptors no Axios 

### Introdução

Os interceptors do Axios permitem que você intercepte as solicitações e respostas HTTP para adicionar lógica personalizada, como autenticação de tokens, logging ou tratamento de erros. 

### Instalação

Primeiro, certifique-se de ter Axios instalado no seu projeto:

```bash
npm install axios
```

### Configuração Básica do Axios

Vamos começar configurando uma instância do Axios para usar em nosso projeto React.

#### Configurando uma Instância do Axios

Crie um arquivo `axiosInstance.ts`:

```typescript
import axios from 'axios';

const axiosInstance = axios.create({
  baseURL: 'https://api.example.com',
  timeout: 10000,
});

export default axiosInstance;
```

### Configurando Interceptors

Os interceptors podem ser usados para adicionar lógica personalizada antes que uma solicitação seja enviada ou antes que uma resposta seja processada.

#### Interceptor de Requisição

Um interceptor de requisição pode ser usado para adicionar cabeçalhos de autenticação ou modificar a configuração da solicitação.

```typescript
import axiosInstance from './axiosInstance';

axiosInstance.interceptors.request.use(
  (config) => {
    // Adicionando um token de autenticação a todas as solicitações
    const token = localStorage.getItem('token');
    if (token) {
      config.headers['Authorization'] = `Bearer ${token}`;
    }
    return config;
  },
  (error) => {
    // Tratamento de erros na solicitação
    return Promise.reject(error);
  }
);
```

#### Interceptor de Resposta

Um interceptor de resposta pode ser usado para lidar com respostas globais, como logging, tratamento de erros ou redirecionamento baseado em códigos de status.

```typescript
import axiosInstance from './axiosInstance';

axiosInstance.interceptors.response.use(
  (response) => {
    // Processar a resposta antes de retorná-la
    return response;
  },
  (error) => {
    // Tratamento de erros na resposta
    if (error.response?.status === 401) {
      // Redirecionar para a página de login em caso de erro de autenticação
      window.location.href = '/login';
    }
    return Promise.reject(error);
  }
);
```

### Usando Interceptors como Hooks

Para tornar o uso dos interceptors mais reutilizável e organizado, você pode encapsular a lógica dos interceptors em hooks personalizados do React. Isso pode ajudar a gerenciar a configuração de interceptors em componentes específicos ou em toda a aplicação.

#### Criando um Hook para Interceptors

Vamos criar um hook chamado `useAxiosInterceptors` que configura os interceptors do Axios:

```typescript
import { useEffect } from 'react';
import axiosInstance from './axiosInstance';

const useAxiosInterceptors = () => {
  useEffect(() => {
    const requestInterceptor = axiosInstance.interceptors.request.use(
      (config) => {
        const token = localStorage.getItem('token');
        if (token) {
          config.headers['Authorization'] = `Bearer ${token}`;
        }
        return config;
      },
      (error) => Promise.reject(error)
    );

    const responseInterceptor = axiosInstance.interceptors.response.use(
      (response) => response,
      (error) => {
        if (error.response?.status === 401) {
          window.location.href = '/login';
        }
        return Promise.reject(error);
      }
    );

    // Cleanup interceptors on unmount
    return () => {
      axiosInstance.interceptors.request.eject(requestInterceptor);
      axiosInstance.interceptors.response.eject(responseInterceptor);
    };
  }, []);
};

export default useAxiosInterceptors;
```

#### Usando o Hook em Componentes

Agora, você pode usar o hook `useAxiosInterceptors` em seus componentes React para configurar automaticamente os interceptors quando o componente for montado:

```typescript
import React, { useEffect, useState } from 'react';
import axiosInstance from './axiosInstance';
import useAxiosInterceptors from './useAxiosInterceptors';

interface User {
  id: number;
  name: string;
  email: string;
}

const UserList: React.FC = () => {
  const [users, setUsers] = useState<User[]>([]);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);

  useAxiosInterceptors();

  useEffect(() => {
    const fetchUsers = async () => {
      try {
        const response = await axiosInstance.get('/users');
        setUsers(response.data);
      } catch (err) {
        setError('Failed to fetch users');
      } finally {
        setLoading(false);
      }
    };

    fetchUsers();
  }, []);

  if (loading) return <div>Loading...</div>;
  if (error) return <div>{error}</div>;

  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            {user.name} ({user.email})
          </li>
        ))}
      </ul>
    </div>
  );
};

export default UserList;
```
