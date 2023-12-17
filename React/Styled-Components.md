# Styled-Components

## Instalação
```bash
# Com npm
npm install styled-components

# Com yarn
yarn add styled-components
```

## Uso Básico

```jsx
import styled from 'styled-components';

// Crie um componente ./styles.js estilizado
const Button = styled.button`
  background-color: #007bff;
  color: #fff;
  font-size: 16px;
  padding: 10px 20px;
  border: none;
  cursor: pointer;

  &:hover {
    background-color: #0056b3;
  }
`;

// Use o componente em seu aplicativo
import {Button} from './styles';

function App() {
  return (
    <div>
      <Button>Styled Button</Button>
    </div>
  );
}
```

### Passando Props

```js
const Button = styled.button`
  background-color: ${(props) => (props.primary ? '#007bff' : '#333')};
  color: #fff;
  font-size: 16px;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
`;
```

```jsx
<Button primary>Primary Button</Button>
<Button>Secondary Button</Button>
```

Ou,

```js
export const ButtonContainer = styled.button`
    background: #565656;
    border-radius: 22px;
    position: relative;

    color: #FFFF;
    padding: 2px 12px;
    min-width: 120px;
    width: 100%;

    ${(props) => (props.variant !== "primary" && `
        min-width: 167px;
        height: 33px;
        background: #E4105D;
    `)};
`
```

```jsx
export default function ({title, variant="primary", onClick}) {
    return (
        <div>
            <ButtonContainer 
                variant={variant}
                onClick={onClick}>
                    {title}
            </ButtonContainer>
        </div>
    )
}  
```

```js
<Button title="Primary Button"/>
<Button title="Secundary Button" variant="secundary"/>
```

### Estilos Globais

```jsx
import { createGlobalStyle } from 'styled-components';

const GlobalStyle = createGlobalStyle`
  body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
  }
`;

function App() {
  return (
    <div>
      <GlobalStyle />
      <p>Hello, world!</p>
    </div>
  );
}
```

### Aninhamento de Estilos

```jsx
const Card = styled.div`
  background-color: #fff;
  padding: 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);

  h2 {
    color: #333;
  }

  p {
    color: #777;
  }
`;
```

### Extensão de Componentes

```jsx
const Button = styled.button`
  /* Estilos aqui */
`;

const PrimaryButton = styled(Button)`
  background-color: #007bff;
  color: #fff;

  &:hover {
    background-color: #0056b3;
  }
`;

<PrimaryButton>Primary Button</PrimaryButton>
```