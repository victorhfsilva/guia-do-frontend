# **React Hook Form**

O React Hook Form é uma biblioteca de gerenciamento de formulários para React que utiliza os Hooks do React para simplificar a criação e validação de formulários de maneira eficiente. 

## Instalação

Para começar a usar o React Hook Form, você pode instalá-lo via npm ou yarn:

```bash
npm install react-hook-form

# ou

yarn add react-hook-form
```

Em typescript também é necessário instalar as tipagens do TypeScript:

```bash
npm install @types/react-hook-form
```

## Uso Básico

### **Formulário**

   - Importe `useForm` do React Hook Form.
   - Chame `useForm()` no componente do formulário para criar um objeto de formulário.

   ```javascript
   import { useForm } from 'react-hook-form';

   function MyForm() {

     const { register, handleSubmit } = useForm();

     // Resto do código do formulário
   }
   ```

## **Campos de Entrada**

   - Utilize o atributo `ref` criado pelo `register` nos campos de entrada.

   - O argumento fornecido para register é o identificador único para o campo de entrada. É através deste identificador que a biblioteca de gerenciamento de formulários rastreia e manipula o campo. Pode ser um nome específico ('fieldName' no exemplo), mas deve ser único dentro do formulário.

   ```javascript
   <input type='text' name='name' ref={register('fieldName')} />
   ```

## **Envio de Formulário**

   - O atributo onSubmit é um evento associado ao formulário que é acionado quando o formulário é enviado. 

   ```javascript
   <form onSubmit={handleSubmit(onSubmit)}>
     {/* Campos de entrada aqui */}
     <button type="submit">Enviar</button>
   </form>
   ```

## Validação

O React Hook Form oferece suporte a várias regras de validação, como `required`, `minLength`, `maxLength`, `pattern` e personalização de validação. Aqui está um exemplo de uso:

```javascript
<input
  ref={register('email', {
    required: 'O email é obrigatório.',
    pattern: {
      value: /^[A-Za-z]+$/i,
      message: 'Somente letras são permitidas no email.',
    }
  })}
/>
<p>{errors.email?.message}</p>
```

### Estados e Erros

- Use o objeto `errors` para rastrear erros de validação.
- Verifique `errors.fieldName` para exibir mensagens de erro associadas a um campo específico.

### Trabalhando com Regras Personalizadas

- Crie funções de validação personalizadas e aplique-as nas regras de validação.

```javascript
const isUniqueEmail = async (email) => {
  const response = await checkEmailAvailability(email);
  return response.available;
};

<input
  ref={register('email', {
    validate: {
      isUnique: isUniqueEmail,
    },
  })}
/>
```

## Formulários Controlados

- Use `useForm` com `defaultValues` para criar definir valores padrão.
- Utilize `setValue` para atualizar valores de campos controlados.

```javascript
const { register, handleSubmit, setValue } = useForm({
  defaultValues: {
    name: 'John',
    email: 'john@example.com',
  }
});
```

## Aninhamento de Dados

- Use notação de ponto para campos aninhados em objetos.

```javascript
<input ref={register('address.street')} />
<input ref={register('address.city')} />
```

### Exemplo

```js
import React from 'react';
import { useForm } from 'react-hook-form';

function App() {
  // Inicialize o hook useForm
  const { register, handleSubmit, errors } = useForm();

  // Função para lidar com o envio do formulário
  const onSubmit = (data) => {
    console.log(data); // Os dados do formulário serão exibidos no console
  };

  return (
    <div className="App">
      <h1>Formulário com React Hook Form</h1>
      <form onSubmit={handleSubmit(onSubmit)}>
        {/* Campo de Nome */}
        <div>
          <label>Nome:</label>
          <input
            type="text"
            name="name"
            ref={register({ required: 'Nome é obrigatório' })}
          />
          {errors.name && <p>{errors.name.message}</p>}
        </div>

        {/* Campo de Email */}
        <div>
          <label>Email:</label>
          <input
            type="text"
            name="email"
            ref={register({
              required: 'Email é obrigatório',
              pattern: {
                value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
                message: 'Email inválido',
              },
            })}
          />
          {errors.email && <p>{errors.email.message}</p>}
        </div>

        {/* Botão de Envio */}
        <div>
          <button type="submit">Enviar</button>
        </div>
      </form>
    </div>
  );
}

export default App;
```

Ou, em tsx:

```tsx
import React from 'react';
import { useForm, SubmitHandler } from 'react-hook-form';

interface FormData {
  name: string;
  email: string;
}

function App() {
  // Inicialize o hook useForm
  const { register, handleSubmit, errors } = useForm<FormData>();

  // Função para lidar com o envio do formulário
  const onSubmit: SubmitHandler<FormData> = (data) => {
    console.log(data); // Os dados do formulário serão exibidos no console
  };

  return (
    <div className="App">
      <h1>Formulário com React Hook Form</h1>
      <form onSubmit={handleSubmit(onSubmit)}>
        {/* Campo de Nome */}
        <div>
          <label>Nome:</label>
          <input
            type="text"
            name="name"
            ref={register({ required: 'Nome é obrigatório' })}
          />
          {errors.name && <p>{errors.name.message}</p>}
        </div>

        {/* Campo de Email */}
        <div>
          <label>Email:</label>
          <input
            type="text"
            name="email"
            ref={register({
              required: 'Email é obrigatório',
              pattern: {
                value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
                message: 'Email inválido',
              },
            })}
          />
          {errors.email && <p>{errors.email.message}</p>}
        </div>

        {/* Botão de Envio */}
        <div>
          <button type="submit">Enviar</button>
        </div>
      </form>
    </div>
  );
}

export default App;
```