# React Router

## Instalação

Instale o React Router no seu projeto usando npm ou yarn:

```bash
# Com npm
npm install react-router-dom

# Com yarn
yarn add react-router-dom
```

Para adicionar tipagens TypeScript:

```bash
yarn add -D @types/react-router-dom
```

## Configuração Básica

### Estrutura de Arquivos

Organize suas páginas em uma estrutura de pastas. Exemplo:

```
src
|-- pages
|   |-- Layout.tsx
|   |-- Home.tsx
|   |-- Blogs.tsx
|   |-- Contact.tsx
|   |-- NoPage.tsx
|-- App.tsx
```

### App.tsx

Configure suas rotas usando o componente `BrowserRouter` e `Routes`. Utilize o componente `Route` para associar caminhos a elementos.

```tsx
// App.tsx

import ReactDOM from "react-dom/client";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Layout from "./pages/Layout";
import Home from "./pages/Home";
import Blogs from "./pages/Blogs";
import Contact from "./pages/Contact";
import NoPage from "./pages/NoPage";

export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Layout />}>
          <Route index element={<Home />} />
          <Route path="blogs" element={<Blogs />} />
          <Route path="contact" element={<Contact />} />
          <Route path="*" element={<NoPage />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}
```

### Layout Component

Crie um componente de layout com navegação compartilhada usando `<Outlet>` e `<Link>`.

- O `<Outlet>` renderiza a rota atual selecionada.
- `<Link>` é usado para definir o URL e acompanhar o histórico de navegação.

```tsx
// Layout.tsx

import { Outlet, Link } from "react-router-dom";

const Layout = () => {
  return (
    <>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/blogs">Blogs</Link>
          </li>
          <li>
            <Link to="/contact">Contact</Link>
          </li>
        </ul>
      </nav>

      <Outlet />
    </>
  );
};

export default Layout;
```

### Páginas

Crie páginas simples para suas rotas.

```tsx
// Home.tsx

const Home = () => {
  return <h1>Home</h1>;
};

export default Home;
```

#### Rota 404 (NoPage)

```tsx
// NoPage.tsx

const NoPage = () => {
  return <h1>404</h1>;
};

export default NoPage;
```

### Navegação

Use o componente `<Link>` para criar links de navegação.

```tsx
<Link to="/path">Link Text</Link>
```

### Parâmetros de Rota

Defina parâmetros em suas rotas.

```tsx
<Route path="/user/:id" element={<User />} />
```

Acessível via `props.match.params.id` no componente `User`.