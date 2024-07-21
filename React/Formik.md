# Formik 

## Introdução

Formik é uma biblioteca popular para construir e gerenciar formulários em React. Ele facilita a manipulação do estado do formulário, validação, e envio, tornando a criação de formulários complexos mais simples e organizada. Este guia abordará como usar Formik para criar e gerenciar formulários em uma aplicação React.

## Configuração do Projeto

### Inicializando o Projeto

Primeiro, crie um novo projeto React com TypeScript. Execute o comando abaixo no terminal:

```bash
npx create-react-app my-formik-app --template typescript
```

### Instalando Formik e Yup

Depois de criar o projeto, navegue até o diretório do projeto e instale o Formik e o Yup para validação de formulários:

```bash
cd my-formik-app
npm install formik yup
```

## Criando um Formulário com Formik

### Estrutura Básica

Vamos criar um formulário simples com campos de nome, email e senha.

#### `components/MyForm.tsx`

```tsx
import React from 'react';
import { Formik, Field, Form, ErrorMessage } from 'formik';
import * as Yup from 'yup';

// Definindo o tipo das props do formulário
interface MyFormValues {
  name: string;
  email: string;
  password: string;
}

// Esquema de validação com Yup
const validationSchema = Yup.object({
  name: Yup.string().required('Required'),
  email: Yup.string().email('Invalid email address').required('Required'),
  password: Yup.string().min(6, 'Password must be at least 6 characters').required('Required'),
});

const MyForm: React.FC = () => {
  const initialValues: MyFormValues = { name: '', email: '', password: '' };

  return (
    <div>
      <h1>My Form</h1>
      <Formik
        initialValues={initialValues}
        validationSchema={validationSchema}
        onSubmit={async (values) => {
            await new Promise((r) => setTimeout(r, 500));
            alert(JSON.stringify(values, null, 2));
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
              <label htmlFor="password">Password</label>
              <Field name="password" type="password" />
              <ErrorMessage name="password" component="div" />
            </div>
            <button type="submit" disabled={isSubmitting}>
              Submit
            </button>
          </Form>
        )}
      </Formik>
    </div>
  );
};

export default MyForm;
```

#### Explicação do Código

1. **Definindo Tipos**: Criamos uma interface `MyFormValues` para definir os tipos dos valores do formulário.

2. **Yup Validation Schema**: Usamos Yup para definir um esquema de validação, garantindo que o nome seja obrigatório, o email seja válido e a senha tenha pelo menos 6 caracteres.

3. **Formik Component**: O componente `Formik` recebe as `initialValues`, o `validationSchema` e a função `onSubmit` como props.

4. **Form Component**: Dentro do Formik, usamos o componente `Form` para envolver os campos do formulário.

5. **Field Component**: O componente `Field` é usado para criar inputs de formulário que estão automaticamente conectados ao estado do Formik.

6. **ErrorMessage Component**: O componente `ErrorMessage` exibe mensagens de erro de validação para os campos correspondentes.


### Usando Formik com Material UI

Formik pode ser integrado com o Material UI utilizando o hook `useFormik`.

```typescript
import { Button, TextField, Typography } from "@mui/material";
import { useFormik } from "formik";
import * as yup from 'yup';

const Form = () => {

    const validationSchema = yup.object().shape({
        name: yup
            .string().required('Name is required.')
            .matches(/^[a-zA-Z]+$/, 'Must only contain letters'),
        email: yup
            .string().required('Email is required.')
            .email('Enter a valid email'),
        password: yup
            .string().required('Password is required.')
            .min(8, 'Password should be of minimum 8 characters length')
            .matches(
                /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[\W_]).+$/,
                'Must contain at least one lowercase letter, one uppercase letter, one number, and one special character'
            )
    })

    const formik = useFormik({
        initialValues: {
            name: '',
            email: '',
            password: ''
        },
        validationSchema: validationSchema,
        onSubmit: (values) => {
            alert(JSON.stringify(values, null, 2))
        }
    })

    return (
        <form onSubmit={formik.handleSubmit}>
            <Typography variant="h1">
                Register User
            </Typography>

            <TextField
                id="name"
                name="name"
                label="Name"
                value={formik.values.name}
                onChange={formik.handleChange}
                onBlur={formik.handleBlur}
                error={formik.touched.name && Boolean(formik.errors.name)}
                helperText={formik.touched.name && formik.errors.name}
            />

            <TextField
                id="email"
                name="email"
                label="Email"
                value={formik.values.email}
                onChange={formik.handleChange}
                onBlur={formik.handleBlur}
                error={formik.touched.email && Boolean(formik.errors.email)}
                helperText={formik.touched.email && formik.errors.email}
            />

            <TextField
                id="password"
                name="password"
                label="Password"
                value={formik.values.password}
                onChange={formik.handleChange}
                onBlur={formik.handleBlur}
                error={formik.touched.password && Boolean(formik.errors.password)}
                helperText={formik.touched.password && formik.errors.password}
            />

            <Button color="primary" variant="contained" type="submit">
                Submit
            </Button>
        </form>
    )
}

export default Form;
```


### Validate

A propriedade `validate` no Formik é uma opção poderosa que permite definir uma função de validação personalizada para os seus formulários. Embora o Formik seja frequentemente usado em conjunto com bibliotecas de validação como Yup, a propriedade `validate` oferece flexibilidade adicional para criar validações personalizadas diretamente no código do Formik.

#### Exemplo Síncrono

```tsx
import React from 'react';
import { Formik, Field, Form, ErrorMessage } from 'formik';

// Definindo o tipo das props do formulário
interface MyFormValues {
  name: string;
  email: string;
  age: number;
}

// Função de validação personalizada
const validate = (values: MyFormValues) => {
  const errors: { [key: string]: string } = {};

  if (!values.name) {
    errors.name = 'Required';
  } else if (values.name.length > 15) {
    errors.name = 'Must be 15 characters or less';
  }

  if (!values.email) {
    errors.email = 'Required';
  } else if (!/\S+@\S+\.\S+/.test(values.email)) {
    errors.email = 'Invalid email address';
  }

  if (!values.age) {
    errors.age = 'Required';
  } else if (values.age < 18) {
    errors.age = 'You must be at least 18 years old';
  }

  return errors;
};

const CustomValidationForm: React.FC = () => {
  const initialValues: MyFormValues = { name: '', email: '', age: 0 };

  return (
    <div>
      <h1>Custom Validation Form</h1>
      <Formik
        initialValues={initialValues}
        validate={validate}
        onSubmit={(values, { setSubmitting }) => {
          console.log('Form data', values);
          setSubmitting(false);
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
    </div>
  );
};

export default CustomValidationForm;
```

#### Exemplo Assíncrono

```typescript
 const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));
 
 const validate = (values) => {
   return sleep(2000).then(() => {
     const errors = {};
     if (['admin', 'null', 'god'].includes(values.username)) {
       errors.username = 'Nice try';
     }
     // ...
     return errors;
   });
 };
```

### Formik Context

O `useFormikContext` é um hook do Formik que permite acessar o contexto do Formik em qualquer componente filho. Isso é extremamente útil quando você precisa interagir com o estado do formulário ou executar ações relacionadas ao formulário fora do componente `<Formik>` ou `<Form>`.

#### Sintaxe Básica

A sintaxe básica do `useFormikContext` é simples. Você o importa do Formik e o usa dentro de um componente funcional para acessar o contexto do Formik.

```tsx
import { useFormikContext } from 'formik';

const MyComponent: React.FC = () => {
  const formik = useFormikContext<MyFormValues>();

  // Agora você pode acessar qualquer coisa do contexto do Formik
  return (
    <div>
      <button onClick={() => formik.submitForm()}>Submit Form</button>
    </div>
  );
};
```

#### Exemplo

```tsx
import React from 'react';
import { useFormikContext } from 'formik';

interface MyFormValues {
  name: string;
  email: string;
  password: string;
}

const SubmitButton: React.FC = () => {
  const { submitForm, isSubmitting } = useFormikContext<MyFormValues>();

  return (
    <button type="button" onClick={submitForm} disabled={isSubmitting}>
      Submit
    </button>
  );
};

export default SubmitButton;
```