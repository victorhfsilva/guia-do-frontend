# **Rotas Protegidas com React Router**

Rotas protegidas são comuns em aplicativos da web, onde você deseja restringir o acesso a certas partes do aplicativo para usuários autenticados. Este guia aborda como criar rotas protegidas usando a biblioteca React Router. Vamos considerar a autenticação como um exemplo, mas você pode adaptar o conceito para outras formas de proteção de rotas, como autorização.

## **Configuração de Autenticação:**

   Antes de criar rotas protegidas, você precisa configurar a autenticação em seu aplicativo. Você pode usar uma solução de autenticação de sua escolha, como JWT, cookies ou qualquer outra.

## **Criando um Componente de Autenticação:**

   Crie um componente chamado `Auth` que verifica se o usuário está autenticado. Este componente pode ser um gancho (hook) personalizado, um contexto ou qualquer outro método de sua preferência.

   ```jsx
   import React, { createContext, useContext, useState } from 'react';

   // Crie um contexto para o estado de autenticação
   const AuthContext = createContext();

   export function AuthProvider({ children }) {
     const [authenticated, setAuthenticated] = useState(false);

     return (
       <AuthContext.Provider value={{ authenticated, setAuthenticated }}>
         {children}
       </AuthContext.Provider>
     );
   }

   export function useAuth() {
     return useContext(AuthContext);
   }
   ```

   Ou, em tsx:

   ```tsx
    import React, { createContext, useContext, useState, ReactNode } from 'react';

    // Crie um contexto para o estado de autenticação
    interface AuthContextProps {
      authenticated: boolean;
      setAuthenticated: React.Dispatch<React.SetStateAction<boolean>>;
    }

    const AuthContext = createContext<AuthContextProps | undefined>(undefined);

    interface AuthProviderProps {
      children: ReactNode;
    }

    export function AuthProvider({ children }: AuthProviderProps) {
      const [authenticated, setAuthenticated] = useState(false);

      return (
        <AuthContext.Provider value={{ authenticated, setAuthenticated }}>
          {children}
        </AuthContext.Provider>
      );
    }

    export function useAuth() {
      const context = useContext(AuthContext);

      if (!context) {
        throw new Error('useAuth must be used within an AuthProvider');
      }

      return context;
    }

   ```

## **Criando Rotas Protegidas:**

   Agora, você pode criar rotas protegidas usando o componente `PrivateRoute`. Este componente verificará se o usuário está autenticado. Se sim, ele renderizará o componente da rota. Caso contrário, redirecionará o usuário para uma página de login.

   ```jsx
   import React from 'react';
   import { Route, Redirect } from 'react-router-dom';
   import { useAuth } from './Auth'; // Importe o contexto de autenticação

   function PrivateRoute({ component: Component, ...rest }) {
     const { authenticated } = useAuth();

     return (
       <Route
         {...rest}
         render={(props) =>
           authenticated ? (
             <Component {...props} />
           ) : (
             <Redirect to="/login" />
           )
         }
       />
     );
   }

   export default PrivateRoute;
   ```

   Ou, em tsx:

   ```tsx
    import React from 'react';
    import { Route, Redirect, RouteProps } from 'react-router-dom';
    import { useAuth } from './Auth'; // Importe o contexto de autenticação

    interface PrivateRouteProps extends RouteProps {
      component: React.ComponentType<any>;
    }

    function PrivateRoute({ component: Component, ...rest }: PrivateRouteProps) {
      const { authenticated } = useAuth();

      return (
        <Route
          {...rest}
          render={(props) =>
            authenticated ? <Component {...props} /> : <Redirect to="/login" />
          }
        />
      );
    }

    export default PrivateRoute;

   ```

5. **Usando Rotas Protegidas:**

   Agora, você pode usar `PrivateRoute` para proteger rotas em seu aplicativo. Importe `PrivateRoute` e defina rotas com base em sua autenticação.

   ```jsx
   import React from 'react';
   import { BrowserRouter as Router, Switch, Route } from 'react-router-dom';
   import PrivateRoute from './PrivateRoute';
   import { AuthProvider } from './Auth';

   import Home from './Home';
   import Dashboard from './Dashboard';
   import Login from './Login';

   function App() {
     return (
       <AuthProvider>
         <Router>
           <Switch>
             <Route path="/login" component={Login} />
             <PrivateRoute path="/dashboard" component={Dashboard} />
             <PrivateRoute exact path="/" component={Home} />
           </Switch>
         </Router>
       </AuthProvider>
     );
   }

   export default App;
   ```

6. **Navegação entre Rotas Protegidas:**

   Você pode criar links ou botões que levam o usuário a rotas protegidas, como o `Dashboard`. Certifique-se de que o usuário esteja autenticado antes de mostrar esses links.

   ```jsx
   import React from 'react';
   import { Link } from 'react-router-dom';
   import { useAuth } from './Auth';

   function Header() {
     const { authenticated } = useAuth();

     return (
       <nav>
         {authenticated && (
           <Link to="/dashboard">Dashboard</Link>
         )}
       </nav>
     );
   }

   export default Header;
   ```

7. **Encerrando a Sessão:**

   Você pode adicionar um botão "Sair" que define o estado de autenticação como falso, encerrando assim a sessão do usuário.

   ```jsx
   import React from 'react';
   import { useAuth } from './Auth';

   function Header() {
     const { authenticated, setAuthenticated } = useAuth();

     const handleLogout = () => {
       setAuthenticated(false);
     };

     return (
       <nav>
         {authenticated && (
           <>
             <Link to="/dashboard">Dashboard</Link>
             <button onClick={handleLogout}>Sair</button>
           </>
         )}
       </nav>
     );
   }

   export default Header;
   ```
