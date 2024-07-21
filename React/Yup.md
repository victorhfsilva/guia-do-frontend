# Validação de Esquemas com o Yup 

## Introdução

Yup é uma biblioteca JavaScript para validação de esquemas de objetos. É amplamente utilizada em conjunto com Formik para validar formulários em aplicações React, mas também pode ser usada de forma independente em qualquer projeto JavaScript.

## Configuração do Projeto

### Inicializando o Projeto

Primeiro, crie um novo projeto Node.js ou React (se você ainda não tiver um):

```bash
npx create-react-app my-yup-app --template typescript
cd my-yup-app
npm install yup
```

## Fundamentos do Yup

### Definindo um Esquema Básico

Um esquema Yup define a estrutura e as regras de validação para um objeto. Vamos criar um esquema simples para um objeto de usuário.

```ts
import * as Yup from 'yup';

// Definindo um esquema Yup para um objeto de usuário
const userSchema = Yup.object().shape({
  name: Yup.string().required('Name is required'),
  email: Yup.string().email('Invalid email address').required('Email is required'),
  age: Yup.number().positive('Age must be a positive number').integer('Age must be an integer').required('Age is required'),
});

// Exemplo de dados para validação
const userData = {
  name: 'John Doe',
  email: 'john.doe@example.com',
  age: 30,
};

// Validando os dados
userSchema.validate(userData)
  .then((valid) => {
    console.log('Validation succeeded:', valid);
  })
  .catch((err) => {
    console.log('Validation failed:', err.errors);
  });
```

### Tipos de Validação

Yup suporta validação de vários tipos de dados, incluindo strings, números, booleans, arrays, objetos, e mais. Aqui estão alguns exemplos de como definir validações para diferentes tipos de dados.

#### Strings

```ts
const stringSchema = Yup.string()
  .required('This field is required')
  .min(3, 'Must be at least 3 characters')
  .max(10, 'Must be at most 10 characters')
  .matches(/^[a-zA-Z]+$/, 'Must only contain letters');
```

#### Números

```ts
const numberSchema = Yup.number()
  .required('This field is required')
  .positive('Must be a positive number')
  .integer('Must be an integer')
  .min(1, 'Must be at least 1')
  .max(100, 'Must be at most 100');
```

#### Booleans

```ts
const booleanSchema = Yup.boolean()
  .required('This field is required')
  .oneOf([true], 'Must be true');
```

#### Arrays

```ts
const arraySchema = Yup.array()
  .of(Yup.string().required('Each item must be a string'))
  .min(1, 'Must have at least one item')
  .max(5, 'Must have at most five items');
```

#### Objetos Aninhados

```ts
const nestedObjectSchema = Yup.object().shape({
  user: Yup.object().shape({
    name: Yup.string().required('Name is required'),
    email: Yup.string().email('Invalid email address').required('Email is required'),
  }),
  age: Yup.number().required('Age is required'),
});
```

### Validação Condicional

Yup permite validação condicional usando a função `when`. Isto é útil quando a validação de um campo depende do valor de outro campo.

```ts
const conditionalSchema = Yup.object().shape({
  isEmployee: Yup.boolean().required('This field is required'),
  employeeId: Yup.string().when('isEmployee', {
    is: true,
    then: Yup.string().required('Employee ID is required'),
    otherwise: Yup.string(),
  }),
});
```

### Validação Assíncrona

Yup suporta validação assíncrona, útil para validações que dependem de chamadas a APIs ou outras operações assíncronas.

```ts
const asyncSchema = Yup.string().test('is-unique', 'Name must be unique', async (value) => {
  const response = await fetch(`https://api.example.com/users?name=${value}`);
  const data = await response.json();
  return data.length === 0;
});
```

### Mensagens de Erro Personalizadas

Você pode definir mensagens de erro personalizadas para cada regra de validação.

```ts
const customMessagesSchema = Yup.object().shape({
  username: Yup.string().required('Please enter your username'),
  password: Yup.string()
    .required('Please enter your password')
    .min(8, 'Password must be at least 8 characters long'),
});
```

### Usando Yup com Formik

Formik integra-se bem com Yup para fornecer validação de formulários. Aqui está um exemplo básico de como usar Yup com Formik.

#### `components/MyForm.tsx`

```tsx
import React from 'react';
import { Formik, Field, Form, ErrorMessage } from 'formik';
import * as Yup from 'yup';

const MyForm: React.FC = () => {
  const initialValues = { name: '', email: '', age: '' };

  const validationSchema = Yup.object().shape({
    name: Yup.string().required('Name is required'),
    email: Yup.string().email('Invalid email address').required('Email is required'),
    age: Yup.number().positive('Age must be a positive number').integer('Age must be an integer').required('Age is required'),
  });

  return (
    <Formik
      initialValues={initialValues}
      validationSchema={validationSchema}
      onSubmit={(values) => {
        console.log('Form data', values);
      }}
    >
      {({ isSubmitting }) => (
        <Form>
          <div>
            <label htmlFor="name">Name</label>
            <Field name="name" type="text" />
            <ErrorMessage name="name" component="div" />
          </div>
          <div>
            <label htmlFor="email">Email</label>
            <Field name="email" type="email" />
            <ErrorMessage name="email" component="div" />
          </div>
          <div>
            <label htmlFor="age">Age</label>
            <Field name="age" type="number" />
            <ErrorMessage name="age" component="div" />
          </div>
          <button type="submit" disabled={isSubmitting}>
            Submit
          </button>
        </Form>
      )}
    </Formik>
  );
};

export default MyForm;
```
