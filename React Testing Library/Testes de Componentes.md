# Testes de Componentes com React Testing Library

## Testes Básicos 

#### Escrevendo Testes

1. Importe as funções necessárias do React Testing Library e os componentes a serem testados.

   ```javascript
   import { render, screen } from '@testing-library/react';
   import MeuComponente from './MeuComponente';
   ```

2. Escreva os testes para verificar o comportamento do componente.

   ```javascript
   describe('MeuComponente', () => {
     it('renderiza corretamente', () => {
       render(<MeuComponente />);
       expect(screen.getByText('Olá Mundo')).toBeInTheDocument();
     });

     it('exibe uma mensagem personalizada', () => {
       render(<MeuComponente mensagem="Bem-vindo" />);
       expect(screen.getByText('Bem-vindo')).toBeInTheDocument();
     });
   });
   ```

#### Código do Componente `<MeuComponente />`

```javascript
import React from 'react';

const MeuComponente = ({ mensagem = 'Olá Mundo' }) => {
  return <div>{mensagem}</div>;
};

export default MeuComponente;
```

## Testes de Interações do Usuário

#### Escrevendo Testes

1. Importe as funções necessárias do React Testing Library e os componentes a serem testados.

   ```javascript
   import { render, screen, fireEvent } from '@testing-library/react';
   import MeuComponente from './MeuComponente';
   ```

2. Escreva os testes para simular e verificar as interações do usuário.

   ```javascript
   describe('MeuComponente', () => {
     it('altera o texto ao clicar no botão', () => {
       render(<MeuComponente />);
       const botao = screen.getByRole('button');
       fireEvent.click(botao);
       expect(screen.getByText('Texto Alterado')).toBeInTheDocument();
     });
   });
   ```

#### Código do Componente `<MeuComponente />`

```javascript
import React, { useState } from 'react';

const MeuComponente = () => {
  const [texto, setTexto] = useState('Texto Original');

  const handleClick = () => {
    setTexto('Texto Alterado');
  };

  return (
    <div>
      <p>{texto}</p>
      <button onClick={handleClick}>Clique Aqui</button>
    </div>
  );
};

export default MeuComponente;
```

## Testes de Componentes Assíncronos

#### Escrevendo Testes

1. Importe as funções necessárias do React Testing Library e os componentes a serem testados.

   ```javascript
   import { render, screen, waitFor } from '@testing-library/react';
   import ComponenteAssincrono from './ComponenteAssincrono';
   ```

2. Escreva os testes para verificar o comportamento do componente assíncrono.

   ```javascript
   describe('ComponenteAssincrono', () => {
     it('renderiza corretamente após uma operação assíncrona', async () => {
       render(<ComponenteAssincrono />);
       // Aguarde até que o elemento seja renderizado após a operação assíncrona
       await waitFor(() => expect(screen.getByText('Dados Carregados')).toBeInTheDocument());
     });
   });
   ```

#### Código do Componente `<ComponenteAssincrono />`

```javascript
import React, { useState, useEffect } from 'react';

const ComponenteAssincrono = () => {
  const [dados, setDados] = useState(null);

  useEffect(() => {
    // Simulando uma operação assíncrona
    setTimeout(() => {
      setDados('Dados Carregados');
    }, 1000);
  }, []);

  return (
    <div>
      <p>{dados}</p>
    </div>
  );
};

export default ComponenteAssincrono;
```

## Testes de Navegação

#### Escrevendo Testes

1. Importe as funções necessárias do React Testing Library, os componentes a serem testados e o `BrowserRouter` do React Router DOM.

   ```javascript
   import { render, screen } from '@testing-library/react';
   import { BrowserRouter } from 'react-router-dom';
   import App from './App';
   ```

2. Escreva os testes para verificar a navegação ao clicar em um link.

   ```javascript
   describe('Navegação', () => {
     it('navega para a página de destino ao clicar no link', () => {
       render(
         <BrowserRouter>
           <App />
         </BrowserRouter>
       );
       const link = screen.getByText('Página de Destino');
       fireEvent.click(link);
       expect(screen.getByText('Esta é a Página de Destino')).toBeInTheDocument();
     });
   });
   ```

#### Código do Aplicativo `<App />`

```javascript
import React from 'react';
import { Route, Switch, Link } from 'react-router-dom';

const PaginaInicial = () => <div>Esta é a Página Inicial<Link to="/destino">Página de Destino</Link></div>;
const PaginaDestino = () => <div>Esta é a Página de Destino</div>;

const App = () => {
  return (
    <Switch>
      <Route path="/" exact component={PaginaInicial} />
      <Route path="/destino" component={PaginaDestino} />
    </Switch>
  );
};

export default App;
```