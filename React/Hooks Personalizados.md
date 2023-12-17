# **Hooks customizados do React**

Hooks customizados são funções que podem ser usadas para gerenciar o estado e outros recursos do React. Eles são uma maneira de abstrair a lógica do componente e torná-la mais reutilizável.

## Primeiros Passos

Para criar um hook customizado, precisamos seguir as seguintes etapas:

1. Criar uma função com a palavra-chave `use` no início.
2. Definir as variáveis de estado e outras variáveis necessárias.
3. Definir os métodos para manipular o estado e outros recursos.


## Exemplo 

Aqui está um exemplo de um hook customizado que alterna um estado entre verdadeiro e falso:

```javascript
function useToggle() {
  const [isToggled, setIsToggled] = useState(false);

  const toggle = () => {
    setIsToggled(!isToggled);
  };

  return {
    isToggled,
    toggle,
  };
}
```

Este hook retorna um objeto com as seguintes propriedades:

* **isToggled:** O estado atual do botão.
* **toggle:** O método para alternar o estado do botão.

### Utilizando o Hook Personalizado

Para usar um hook customizado, precisamos importá-lo e chamá-lo no componente:

```javascript
import React, { useState } from 'react';
import useToggle from './useToggle';

const App = () => {

  const { isToggled, toggle } = useToggle();

  return (
    <div>
      <button onClick={toggle}>
        {isToggled ? 'Desligado' : 'Ligado'}
      </button>
    </div>
  );
};
```

Neste exemplo, o hook `useToggle` é usado para controlar o estado de um botão. O botão alterna entre o texto "Ligado" e "Desligado" quando é clicado.
