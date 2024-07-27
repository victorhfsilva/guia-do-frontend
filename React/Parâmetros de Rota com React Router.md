# Parâmetros de Rota no React Router

## Definindo as Rotas

Primeiro, definimos nossas rotas no componente principal da aplicação:

```tsx
import React from 'react';
import {
  BrowserRouter as Router,
  Route,
  Switch
} from 'react-router-dom';
import HomePage from './HomePage';
import UserPage from './UserPage';

const App: React.FC = () => (
  <Router>
    <Switch>
      <Route path="/" exact component={HomePage} />
      <Route path="/user/:id" component={UserPage} />
    </Switch>
  </Router>
);

export default App;
```

## Acessando Parâmetros de Rota

No React Router, os parâmetros de rota podem ser acessados usando o `useParams` do `react-router-dom`. Vamos criar uma página de usuário (`UserPage`) que acessa o parâmetro `id` da rota.

### UserPage.tsx

```tsx
import React from 'react';
import { useParams } from 'react-router-dom';

interface UserPageParams {
  id: string;
}

const UserPage: React.FC = () => {
  const { id } = useParams<UserPageParams>();

  return (
    <div>
      <h1>User Page</h1>
      <p>User ID: {id}</p>
    </div>
  );
};

export default UserPage;
```

### Explicação

1. **Definição da Interface**: Definimos uma interface `UserPageParams` que descreve os parâmetros esperados na rota (`id` no caso).
2. **useParams Hook**: Utilizamos o hook `useParams` do React Router para acessar os parâmetros da rota, tipando-os com `UserPageParams`.

## Tipando Parâmetros Opcionais

Parâmetros de rota podem ser opcionais. Para isso, usamos o operador `?` na definição da interface.

### Exemplo

```tsx
interface UserPageParams {
  id?: string;
}

const UserPage: React.FC = () => {
  const { id } = useParams<UserPageParams>();

  return (
    <div>
      <h1>User Page</h1>
      {id ? <p>User ID: {id}</p> : <p>No User ID provided</p>}
    </div>
  );
};
```

## Parâmetros Múltiplos

Também podemos definir vários parâmetros em uma única rota.

### Exemplo

```tsx
<Route path="/user/:id/post/:postId">
  <UserPostPage />
</Route>
```

Para acessar esses parâmetros, definimos a interface correspondente:

### UserPostPage.tsx

```tsx
import React from 'react';
import { useParams } from 'react-router-dom';

interface UserPostPageParams {
  id: string;
  postId: string;
}

const UserPostPage: React.FC = () => {
  const { id, postId } = useParams<UserPostPageParams>();

  return (
    <div>
      <h1>User Post Page</h1>
      <p>User ID: {id}</p>
      <p>Post ID: {postId}</p>
    </div>
  );
};

export default UserPostPage;
```

## Query Parameters

### Acessando Query Parameters

Podemos acessar os query parameters usando o hook `useLocation` do `react-router-dom` e a interface `URLSearchParams`.

```tsx
import React from 'react';
import { useLocation } from 'react-router-dom';

const useQuery = () => {
  return new URLSearchParams(useLocation().search);
}

const UserPage: React.FC = () => {
  const query = useQuery();
  const name = query.get('name');

  return (
    <div>
      <h1>User Page</h1>
      <p>Name: {name}</p>
    </div>
  );
};

export default UserPage;
```

### Múltiplos Query Parameters

Podemos passar múltiplos query parameters na URL e acessá-los da mesma forma.

#### Exemplo

```tsx
navigateTo(`/user?name=${name}&age=${age}`);
```

#### Acessando Vários Parâmetros

```tsx
const name = query.get('name');
const age = query.get('age');
```
