# React Input Mask 

`react-input-mask` é uma biblioteca popular para mascarar entradas de usuário em formulários React. Ela permite formatar entradas de texto, como números de telefone, CPF, datas e muito mais, de forma que os usuários insiram dados em um formato específico.

### Instalação

Para começar a usar `react-input-mask`, você precisa instalá-la no seu projeto React. Você pode fazer isso usando npm ou yarn:

```bash
npm install react-input-mask
```
ou
```bash
yarn add react-input-mask
```

### Uso Básico

Aqui está um exemplo básico de como usar `react-input-mask` para criar uma máscara de entrada de telefone:

```jsx
import React from 'react';
import InputMask from 'react-input-mask';

const PhoneInput = () => {
  return (
    <InputMask mask="(99) 99999-9999" placeholder="(XX) XXXXX-XXXX">
      {(inputProps) => <input {...inputProps} type="text" />}
    </InputMask>
  );
};

export default PhoneInput;
```

### Máscaras Comuns

1. **CPF**: `mask="999.999.999-99"`
2. **Data**: `mask="99/99/9999"`
3. **CEP**: `mask="99999-999"`
4. **Cartão de Crédito**: `mask="9999 9999 9999 9999"`

### Props e Métodos

`react-input-mask` vem com várias propriedades e métodos úteis:

- **mask**: Define a máscara de entrada.
- **maskChar**: Define o caractere usado para substituir entradas não digitadas. O padrão é `_`.
- **alwaysShowMask**: Se verdadeiro, a máscara é sempre mostrada, mesmo quando o campo está vazio.
- **beforeMaskedValueChange**: Função chamada antes de o valor mascarado ser alterado. Pode ser usada para validar ou modificar a entrada.
- **formatChars** : Define as chaves correspondentes a cada Regex. As chaves padrão são:

```typescript
formatChars: {
  '9': '[0-9]',
  'a': '[A-Za-z]',
  '*': '[A-Za-z0-9]'
}
```
### beforeMaskedValueChange

Aqui está um exemplo mais avançado que utiliza várias propriedades e métodos:

```jsx
import React, { useState } from 'react';
import InputMask from 'react-input-mask';

const CreditCardInput = () => {
  const [cardNumber, setCardNumber] = useState('');

  const handleBeforeMaskedValueChange = (newState, oldState, userInput) => {
    let { value } = newState;
    if (value.startsWith('34') || value.startsWith('37')) {
      newState.mask = '9999 999999 99999';
    } else {
      newState.mask = '9999 9999 9999 9999';
    }
    return newState;
  };

  return (
    <InputMask
      mask="9999 9999 9999 9999"
      value={cardNumber}
      onChange={(e) => setCardNumber(e.target.value)}
      beforeMaskedValueChange={handleBeforeMaskedValueChange}
    >
      {(inputProps) => <input {...inputProps} type="text" placeholder="XXXX XXXX XXXX XXXX" />}
    </InputMask>
  );
};

export default CreditCardInput;
```

### Configuração Básica de um Formulário

Vamos configurar um formulário básico usando `react-hook-form`.

**Criar o arquivo `Form.tsx`:**

```tsx
import React from 'react';
import { useForm, SubmitHandler } from 'react-hook-form';

type FormValues = {
  phoneNumber: string;
};

const Form: React.FC = () => {
  const { register, handleSubmit, formState: { errors } } = useForm<FormValues>();

  const onSubmit: SubmitHandler<FormValues> = data => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <div>
        <label htmlFor="phoneNumber">Phone Number</label>
        <input id="phoneNumber" {...register('phoneNumber', { required: 'Phone number is required' })} />
        {errors.phoneNumber && <p>{errors.phoneNumber.message}</p>}
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

export default Form;
```

#### Adicionando a Máscara de Entrada

Agora, vamos adicionar a máscara de entrada ao campo de número de telefone usando `react-input-mask`.

**Atualizar o componente `Form.tsx` para incluir a máscara de entrada:**

```tsx
import React from 'react';
import { useForm, SubmitHandler } from 'react-hook-form';
import InputMask from 'react-input-mask';

type FormValues = {
  phoneNumber: string;
};

const Form: React.FC = () => {
  const { register, handleSubmit, setValue, formState: { errors } } = useForm<FormValues>();

  const onSubmit: SubmitHandler<FormValues> = data => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <div>
        <label htmlFor="phoneNumber">Phone Number</label>
        <InputMask
          mask="(99) 99999-9999"
          maskChar=" "
          onChange={(e) => setValue('phoneNumber', e.target.value)}
        >
          {(inputProps) => <input {...register('phoneNumber', { required: 'Phone number is required' })} {...inputProps} />}
        </InputMask>
        {errors.phoneNumber && <p>{errors.phoneNumber.message}</p>}
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

export default Form;
```

Neste exemplo, utilizamos o componente `InputMask` da biblioteca `react-input-mask` para aplicar a máscara de número de telefone. A máscara `(99) 99999-9999` formata o campo como um número de telefone brasileiro.
