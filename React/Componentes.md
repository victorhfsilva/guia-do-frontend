# Componentes de Classe e de Função em React

React é uma biblioteca JavaScript popular para a criação de interfaces de usuário interativas e reativas. Os componentes são a unidade fundamental de qualquer aplicativo React. Eles podem ser escritos como componentes de classe ou como componentes de função. Abordaremos cada um desses tipo a seguir.

## Componentes de Classe

### Sintaxe

```javascript
import React, { Component } from 'react';

class MinhaClasse extends Component {
  render() {
    return (
      <div>
        Componente de Classe
      </div>
    );
  }
}
```

### Estado (State)

- Podem conter um estado interno.
- O estado é definido no método `constructor` usando `this.state`.
- Use `this.setState()` para atualizar o estado e re-renderizar o componente.

### Ciclo de Vida (Lifecycle)

- Possui métodos do ciclo de vida, como `componentDidMount`, `componentDidUpdate`, etc.
- Útil para tarefas como carregar dados de APIs ou manipulação direta do DOM.

### Propriedades (Props)

- As propriedades são acessadas usando `this.props`.
- São imutáveis (não podem ser modificadas pelo componente).

### Referência ao DOM (Ref)

- Pode criar referências a elementos DOM usando `React.createRef()`.
- Útil para interagir diretamente com elementos do DOM.

### Exemplo

```jsx
import React, { Component } from 'react';

class ClasseComEstado extends Component {
  constructor(props) {
    super(props);
    this.state = {
      contador: 0
    };
  }

  render() {
    return (
      <div>
        <p>Contador: {this.state.contador}</p>
        <button onClick={() => this.incrementar()}>Incrementar</button>
      </div>
    );
  }

  incrementar() {
    this.setState({ contador: this.state.contador + 1 });
  }
}
```

Ou, em tsx:

```tsx
import React, { Component } from 'react';

interface Estado {
  contador: number;
}

interface MeuProps {
  mensagem: string;
}

class ClasseComEstado extends Component<MeuProps, Estado> {
  constructor(props: MeuProps) {
    super(props);
    this.state = {
      contador: 0,
    };
  }

  render() {
    return (
      <div>
        <p>{this.props.mensagem}<p>
        <p>Contador: {this.state.contador}</p>
        <button onClick={() => this.incrementar()}>Incrementar</button>
      </div>
    );
  }

  incrementar() {
    this.setState({ contador: this.state.contador + 1 });
  }
}

export default ClasseComEstado;
```

## Componentes de Função

### Sintaxe

```jsx
import React from 'react';

export default function MeuComponente() {
  return (
    <div>
      <p>Hello World<p>
    </div>
  );
}
```

### Utilizando props como argumentos:

```tsx
interface IProps {
  name: String,
  color?: String
};

export default function MeuComponente(props: IProps) {
  return (
    <div>
      <p style={{color:props.color}}>Hello, {props.name}<p>
    </div>
  );
}
```

### Destructuring do props

```tsx
interface IProps {
  name: String,
  color?: String
};

export default const MeuComponent = ({name}: IProps) => {
  return (
    <div>
      <p style={{color:props.color}}>Hello, {name}<p>
    </div>
  )
}
```
### Passando todos o props para um Componente Filho com `...props`

Se você quiser passar todos os props recebidos por um componente pai diretamente para um componente filho, você pode fazer isso de forma mais direta:

```javascript
import React from 'react';

// Define o componente funcional que receberá os props
const MyComponent = ({ text, number, onClick }) => {
  return (
    <div>
      <p>{text}</p>
      <p>{number}</p>
      <button onClick={onClick}>Click me</button>
    </div>
  );
};

// Define o componente pai que passará todos os props para MyComponent usando o operador de espalhamento
const ParentComponent = (props) => {
  return <MyComponent {...props} />;
};

// Uso do componente pai com todos os props
const App = () => {
  return (
    <ParentComponent
      text="Hello, world!"
      number={42}
      onClick={() => alert('Button clicked!')}
    />
  );
};

export default App;
```


### Estado (State)

- Não pode conter um estado interno.
- Use o Hook `useState` para gerenciar estados do React.

### Ciclo de Vida (Lifecycle)

- Não têm métodos de ciclo de vida.
- Em vez disso, utilize Hooks como `useEffect` para efeitos colaterais.

### Propriedades (Props)

- As propriedades são passadas como argumentos para a função.
- São imutáveis (não podem ser modificadas pelo componente).

### Referência ao DOM (Ref)

- Não possui suporte direto para referências a elementos DOM. Use `useRef` para isso.

### Exemplo

```jsx
import React, { useState } from 'react';

function FuncaoComEstado() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Contador: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>Incrementar</button>
    </div>
  );
}
```

Ou, em tsx:

```tsx
import React, { useState } from 'react';

function FuncaoComEstado() {
  const [contador, setContador] = useState<number>(0);

  return (
    <div>
      <p>Contador: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>Incrementar</button>
    </div>
  );
}
```

## Quando Usar Componentes de Classe vs. de Função

- **Componentes de Classe**: Use quando precisar de estados locais complexos, gerenciamento avançado do ciclo de vida ou referências ao DOM.

- **Componentes de Função**: Use em componentes simples, para melhor desempenho ou quando for trabalhar com Hooks.

Com as atualizações mais recentes do React, os componentes de função com Hooks estão se tornando a escolha padrão na maioria dos casos devido à simplicidade e legibilidade.