# Estilização em React

## Estilo Inline

Para aplicar estilos inline em um elemento React, utilize o atributo `style` com um objeto JavaScript contendo as propriedades de estilo:

```jsx
const Header = () => {
  return (
    <>
      <h1 style={{ color: "red" }}>Olá, Estilo!</h1>
      <p>Adicione um pouco de estilo!</p>
    </>
  );
};
```

- Expressões JavaScript são envolvidas por chaves duplas (`{{}}`).
- Propriedades camelCased são usadas para estilos com hífen (por exemplo, `backgroundColor` em vez de `background-color`).

## Folhas de Estilo CSS

Você pode escrever suas folhas de estilo CSS em um arquivo separado com a extensão `.css` e importá-lo no seu aplicativo:

```css
/* App.css */
body {
  background-color: #282c34;
  color: white;
  padding: 40px;
  font-family: Sans-Serif;
  text-align: center;
}
```

```jsx
// index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import './App.css';

const Header = () => {
  return (
    <>
      <h1>Olá, Estilo!</h1>
      <p>Adicione um pouco de estilo!</p>
    </>
  );
};
```

### Módulos CSS

Os Módulos CSS oferecem uma maneira de adicionar estilos encapsulados para componentes em arquivos separados. Cada módulo é exclusivo para o componente que o importa:

```css
/* my-style.module.css */
.bigblue {
  color: DodgerBlue;
  padding: 40px;
  font-family: Sans-Serif;
  text-align: center;
}
```

```jsx
// Car.js
import styles from './my-style.module.css';

const Car = () => {
  return <h1 className={styles.bigblue}>Olá, Carro!</h1>;
};

export default Car;
```

**Observações:**

- **Estilo Inline:** Útil para estilos específicos de um componente.
- **Folhas de Estilo CSS:** Boa para aplicar estilos globalmente.
- **Módulos CSS:** Ótimos para estilos encapsulados por componente.