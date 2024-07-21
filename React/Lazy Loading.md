# React.lazy 

## Introdução

`React.lazy` e `Suspense` são funcionalidades do React que permitem o carregamento dinâmico (lazy loading) de componentes. Isso pode melhorar o desempenho da aplicação, especialmente quando lidamos com grandes componentes ou bibliotecas que não são necessários imediatamente. Este guia abordará como usar `React.lazy` e `Suspense` com TypeScript.

## Usando `React.lazy`

### Importação Dinâmica

Vamos criar dois componentes simples e carregá-los dinamicamente usando `React.lazy`.

#### `components/HeavyComponentA.tsx`

```tsx
import React from 'react';

const HeavyComponentA: React.FC = () => {
  return <div>Heavy Component A Loaded</div>;
};

export default HeavyComponentA;
```

#### `components/HeavyComponentB.tsx`

```tsx
import React from 'react';

const HeavyComponentB: React.FC = () => {
  return <div>Heavy Component B Loaded</div>;
};

export default HeavyComponentB;
```

### Carregando Componentes com `React.lazy`

Vamos usar `React.lazy` para carregar esses componentes dinamicamente no componente pai.

#### `App.tsx`

```tsx
import React, { Suspense, useState } from 'react';

const LazyComponentA = React.lazy(() => import('./components/HeavyComponentA'));
const LazyComponentB = React.lazy(() => import('./components/HeavyComponentB'));

const App: React.FC = () => {
  const [showComponentA, setShowComponentA] = useState(false);
  const [showComponentB, setShowComponentB] = useState(false);

  return (
    <div>
      <h1>React.lazy and Suspense Example</h1>
      <button onClick={() => setShowComponentA(true)}>Load Component A</button>
      <button onClick={() => setShowComponentB(true)}>Load Component B</button>

      <Suspense fallback={<div>Loading...</div>}>
        {showComponentA && <LazyComponentA />}
        {showComponentB && <LazyComponentB />}
      </Suspense>
    </div>
  );
};

export default App;
```

### Usando `Suspense`

O componente `Suspense` é usado para mostrar um fallback (componente de carregamento) enquanto o componente dinâmico está sendo carregado.

No exemplo acima, usamos `Suspense` para envolver nossos componentes carregados dinamicamente. O fallback será exibido enquanto o componente está sendo carregado.

#### `App.tsx` (trecho relevante)

```tsx
<Suspense fallback={<div>Loading...</div>}>
  {showComponentA && <LazyComponentA />}
  {showComponentB && <LazyComponentB />}
</Suspense>
```

#### Múltiplos Suspenses

Você pode usar múltiplos `Suspense` para diferentes componentes ou seções da sua aplicação.

```tsx
import React, { Suspense, useState } from 'react';

const LazyComponentA = React.lazy(() => import('./components/HeavyComponentA'));
const LazyComponentB = React.lazy(() => import('./components/HeavyComponentB'));

const App: React.FC = () => {
  const [showComponentA, setShowComponentA] = useState(false);
  const [showComponentB, setShowComponentB] = useState(false);

  return (
    <div>
      <h1>React.lazy and Suspense Example</h1>
      <button onClick={() => setShowComponentA(true)}>Load Component A</button>
      <button onClick={() => setShowComponentB(true)}>Load Component B</button>

      <Suspense fallback={<div>Loading Component A...</div>}>
        {showComponentA && <LazyComponentA />}
      </Suspense>

      <Suspense fallback={<div>Loading Component B...</div>}>
        {showComponentB && <LazyComponentB />}
      </Suspense>
    </div>
  );
};

export default App;
```

### Conclusão

`React.lazy` e `Suspense` são ferramentas poderosas para otimizar o carregamento de componentes em uma aplicação React. Com o uso correto, você pode melhorar significativamente a performance da sua aplicação, carregando componentes apenas quando eles são necessários.