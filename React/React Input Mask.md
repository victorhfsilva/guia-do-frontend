# React Input Mask

## Instalação

### Usando npm
Para instalar o `react-input-mask` via npm, utilize o seguinte comando:

```bash
npm install react-input-mask 
npm install @types/react-input-mask
```

### Sem um Bundler de Módulo
Você também pode usar o `react-input-mask` diretamente em um projeto sem um bundler de módulo. Basta carregar os scripts do React, React-DOM e React Input Mask:

```html
<!-- Carregar React primeiro -->
<script src="https://unpkg.com/react/dist/react.min.js"></script>
<script src="https://unpkg.com/react-dom/dist/react-dom.min.js"></script>
<!-- Será exportado para window.ReactInputMask -->
<script src="https://unpkg.com/react-input-mask/dist/react-input-mask.min.js"></script>
```

## Propriedades

### mask : string
Define a máscara para o input. Os caracteres padrão são:
- `9`: 0-9
- `a`: A-Z, a-z
- `*`: A-Z, a-z, 0-9

Qualquer caractere pode ser escapado com uma barra invertida (`\`). Ele aparecerá como uma dupla barra invertida em strings JS. Por exemplo, uma máscara de telefone alemão com prefixo fixo +49 ficaria assim: `mask="+4\9 99 999 99"` ou `mask={'+4\\9 99 999 99'}`.

### maskChar : string
Caractere para cobrir partes não preenchidas da máscara. O caractere padrão é "_". Se configurado como `null` ou string vazia, as partes não preenchidas ficarão vazias como em um input comum.

### formatChars : object
Define caracteres de formatação com chaves como caracteres e valores correspondentes em expressões regulares. Os padrões são:

```javascript
{
  '9': '[0-9]',
  'a': '[A-Za-z]',
  '*': '[A-Za-z0-9]'
}
```

### alwaysShowMask : boolean
Mostra a máscara quando o input está vazio e não tem foco.

### inputRef : function
Use `inputRef` ao invés de `ref` se você precisar gerenciar o nó do input para focar, selecionar, etc.

## Propriedades Experimentais

### beforeMaskedValueChange : function
Para comportamentos de máscara mais complexos, você pode fornecer uma função `beforeMaskedValueChange` para alterar o valor mascarado e a posição do cursor antes de serem aplicados ao input. A função recebe os seguintes argumentos:

- `newState` (objeto): Novo estado do input, contendo `value` e `selection`. Exemplo: `{ value: '12/1_/____', selection: { start: 4, end: 4 } }`
- `oldState` (objeto): Estado do input antes da mudança, contendo `value` e `selection`.
- `userInput` (string): String digitada ou colada pelo usuário. `null` se não houver entrada.
- `maskOptions` (objeto): Opções da máscara. Exemplo:
```javascript
{
  mask: '99/99/9999',
  maskChar: '_',
  alwaysShowMask: false,
  formatChars: {
    '9': '[0-9]',
    'a': '[A-Za-z]',
    '*': '[A-Za-z0-9]'
  },
  permanents: [2, 5] // índices dos caracteres não editáveis na máscara
}
```

`beforeMaskedValueChange` deve retornar um objeto com os campos:
- `value` (string): Novo valor.
- `selection` (objeto): Nova seleção.

### children : function
Para usar outro componente em vez de um `<input />` regular, passe uma função `render` como `children`. A função recebe um argumento `props` contendo as propriedades que não são usadas internamente pelo `react-input-mask`.

## Exemplos

### Exemplo Básico

```javascript
import React from 'react';
import InputMask from 'react-input-mask';

class PhoneInput extends React.Component {
  render() {
    return <InputMask {...this.props} mask="+4\9 99 999 99" maskChar=" " />;
  }
}
```

### Usando `beforeMaskedValueChange`

```javascript
import React from 'react';
import InputMask from 'react-input-mask';

class Input extends React.Component {
  state = {
    value: ''
  }

  onChange = (event) => {
    this.setState({
      value: event.target.value
    });
  }

  beforeMaskedValueChange = (newState, oldState, userInput) => {
    var { value } = newState;
    var selection = newState.selection;
    var cursorPosition = selection ? selection.start : null;

    if (value.endsWith('-') && userInput !== '-' && !this.state.value.endsWith('-')) {
      if (cursorPosition === value.length) {
        cursorPosition--;
        selection = { start: cursorPosition, end: cursorPosition };
      }
      value = value.slice(0, -1);
    }

    return {
      value,
      selection
    };
  }

  render() {
    return (
      <InputMask
        mask="99999-9999"
        maskChar={null}
        value={this.state.value}
        onChange={this.onChange}
        beforeMaskedValueChange={this.beforeMaskedValueChange}
      />
    );
  }
}
```

### Integrando com Material-UI

```javascript
import React from 'react';
import InputMask from 'react-input-mask';
import MaterialInput from '@material-ui/core/Input';

// Exemplo funcional
const Input = (props) => (
  <InputMask mask="99/99/9999" value={props.value} onChange={props.onChange}>
    {(inputProps) => <MaterialInput {...inputProps} type="tel" disableUnderline />}
  </InputMask>
);

// Exemplo inválido
const InvalidInput = (props) => (
  <InputMask mask="99/99/9999" value={props.value}>
    {(inputProps) => <MaterialInput {...inputProps} type="tel" disableUnderline onChange={props.onChange} />}
  </InputMask>
);
```