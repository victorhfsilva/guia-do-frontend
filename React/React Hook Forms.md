# React Hook Form

### Introdução

React Hook Form é uma biblioteca poderosa para gerenciar formulários em React. Ele reduz a quantidade de código necessária para gerenciar a lógica de formulários e é altamente eficiente. Quando combinado com TypeScript, podemos aproveitar a tipagem estática para criar formulários robustos e menos propensos a erros.

### Instalação

Primeiro, você precisa instalar o React Hook Form e TypeScript no seu projeto:

```bash
npm install react-hook-form
npm install typescript @types/react
```

### Configuração Inicial

Crie um novo arquivo TypeScript para o seu componente de formulário. Por exemplo, `MyForm.tsx`:

```tsx
import React from 'react';
import { useForm, SubmitHandler } from 'react-hook-form';

interface IFormInput {
  firstName: string;
  lastName: string;
  age: number;
}

const MyForm: React.FC = () => {
  const { register, handleSubmit, formState: { errors } } = useForm<IFormInput>();

  const onSubmit: SubmitHandler<IFormInput> = data => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <div>
        <label>First Name</label>
        <input {...register("firstName", { required: true })} />
        {errors.firstName && <span>This field is required</span>}
      </div>
      
      <div>
        <label>Last Name</label>
        <input {...register("lastName", { required: true })} />
        {errors.lastName && <span>This field is required</span>}
      </div>
      
      <div>
        <label>Age</label>
        <input type="number" {...register("age", { required: true, min: 18 })} />
        {errors.age && <span>Age must be at least 18</span>}
      </div>
      
      <button type="submit">Submit</button>
    </form>
  );
};

export default MyForm;
```

### Adicionando Mais Validações

Você pode adicionar validações mais complexas usando os métodos de validação fornecidos pelo React Hook Form. Por exemplo:

```tsx
<input
  {...register("age", {
    required: "Age is required",
    min: {
      value: 18,
      message: "You must be at least 18 years old"
    }
  })}
/>
{errors.age && <span>{errors.age.message}</span>}
```

### Integração com Bibliotecas de UI

React Hook Form é compatível com várias bibliotecas de UI, como Material-UI, Ant Design, entre outras. Aqui está um exemplo com Material-UI:

```tsx
import React from 'react';
import { useForm, SubmitHandler } from 'react-hook-form';
import { TextField, Button } from '@material-ui/core';

interface IFormInput {
  firstName: string;
  lastName: string;
  age: number;
}

const MyForm: React.FC = () => {
  const { register, handleSubmit, formState: { errors } } = useForm<IFormInput>();

  const onSubmit: SubmitHandler<IFormInput> = data => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <TextField
        label="First Name"
        {...register("firstName", { required: "First Name is required" })}
        error={!!errors.firstName}
        helperText={errors.firstName ? errors.firstName.message : ""}
      />
      
      <TextField
        label="Last Name"
        {...register("lastName", { required: "Last Name is required" })}
        error={!!errors.lastName}
        helperText={errors.lastName ? errors.lastName.message : ""}
      />
      
      <TextField
        label="Age"
        type="number"
        {...register("age", { required: "Age is required", min: { value: 18, message: "You must be at least 18" } })}
        error={!!errors.age}
        helperText={errors.age ? errors.age.message : ""}
      />
      
      <Button type="submit" variant="contained" color="primary">
        Submit
      </Button>
    </form>
  );
};

export default MyForm;
```

### Validações Personalizadas 

Além das validações básicas como `required` e `pattern`, React Hook Form permite criar validações personalizadas para atender necessidades específicas da sua aplicação. Isso pode incluir regras complexas que não são facilmente expressas com validações embutidas.

#### Exemplo

Suponha que você queira validar que a senha deve conter pelo menos uma letra maiúscula, um número e ter pelo menos 8 caracteres. Você pode criar uma validação personalizada para isso.

```tsx
import { useState } from 'react';
import './styles.css';
import { SubmitHandler, useForm } from 'react-hook-form';

const Form = () => {
    type DataType = {
        name: string,
        email: string,
        password: string
    }

    const { register, handleSubmit, formState: { errors } } = useForm<DataType>();

    const onSubmit: SubmitHandler<DataType> = (data) => {
        console.log(data);
    }

    // Função de validação personalizada
    const validatePassword = (value: string) => {
        const hasUpperCase = /[A-Z]/.test(value);
        const hasNumber = /\d/.test(value);
        const minLength = value.length >= 8;

        if (!hasUpperCase) {
            return "Password must have at least one uppercase letter";
        }
        if (!hasNumber) {
            return "Password must have at least one number";
        }
        if (!minLength) {
            return "Password must be at least 8 characters long";
        }
        return true;
    };

    return (
        <div className='form-div'>
            <h2>Register User</h2>
            <form onSubmit={handleSubmit(onSubmit)}>
                <div className='input-div'>
                    <label htmlFor="name">Name: </label>
                    <input type="text" id="name" {...register("name", { required: "Name is required" })} />
                    {errors.name && <p>{errors.name.message}</p>}
                </div>

                <div className='input-div'>
                    <label htmlFor="email">Email: </label>
                    <input type="text" id="email" {...register("email", {
                        required: "Email is required",
                        pattern: {
                            value: /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/,
                            message: "Invalid email address"
                        }
                    })} />
                    {errors.email && <p>{errors.email.message}</p>}
                </div>

                <div className='input-div'>
                    <label htmlFor="password">Password: </label>
                    <input type="password" id="password" {...register("password", {
                        required: "Password is required",
                        validate: validatePassword
                    })} />
                    {errors.password && <p>{errors.password.message}</p>}
                </div>

                <div className='button-div'>
                    <button type="submit">
                        Submit
                    </button>
                </div>
            </form>
        </div>
    )
};

export default Form;
```

## Validações Referenciando Outros Campos

Uma necessidade comum em formulários é validar um campo em relação a outro. Um exemplo clássico é a confirmação de senha, onde precisamos garantir que o campo "Confirmar Senha" seja igual ao campo "Senha". Com React Hook Form e TypeScript, podemos implementar isso de maneira eficiente utilizando a API de validação de formulários.

Para validar que a confirmação de senha é igual à senha, podemos usar o hook `useFormContext` ou acessar diretamente o valor do campo de senha dentro da função de validação personalizada do campo de confirmação de senha. 

### Exemplo

Aqui está um exemplo completo de um formulário de registro com a validação de confirmação de senha:

```tsx
import { useState } from 'react';
import './styles.css';
import { SubmitHandler, useForm } from 'react-hook-form';

const Form = () => {
    type DataType = {
        name: string,
        email: string,
        password: string,
        confirmPassword: string
    }

    const { register, handleSubmit, watch, formState: { errors } } = useForm<DataType>();

    const onSubmit: SubmitHandler<DataType> = (data) => {
        console.log(data);
    }

    // Função de validação personalizada para confirmar senha
    const validateConfirmPassword = (value: string) => {
        const password = watch('password'); // Obtém o valor do campo de senha
        if (value !== password) {
            return "Passwords do not match";
        }
        return true;
    };

    return (
        <div className='form-div'>
            <h2>Register User</h2>
            <form onSubmit={handleSubmit(onSubmit)}>
                <div className='input-div'>
                    <label htmlFor="name">Name: </label>
                    <input type="text" id="name" {...register("name", { required: "Name is required" })} />
                    {errors.name && <p>{errors.name.message}</p>}
                </div>

                <div className='input-div'>
                    <label htmlFor="email">Email: </label>
                    <input type="text" id="email" {...register("email", {
                        required: "Email is required",
                        pattern: {
                            value: /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/,
                            message: "Invalid email address"
                        }
                    })} />
                    {errors.email && <p>{errors.email.message}</p>}
                </div>

                <div className='input-div'>
                    <label htmlFor="password">Password: </label>
                    <input type="password" id="password" {...register("password", {
                        required: "Password is required",
                        validate: {
                            hasUpperCase: value => /[A-Z]/.test(value) || "Password must have at least one uppercase letter",
                            hasNumber: value => /\d/.test(value) || "Password must have at least one number",
                            minLength: value => value.length >= 8 || "Password must be at least 8 characters long"
                        }
                    })} />
                    {errors.password && <p>{errors.password.message}</p>}
                </div>

                <div className='input-div'>
                    <label htmlFor="confirmPassword">Confirm Password: </label>
                    <input type="password" id="confirmPassword" {...register("confirmPassword", {
                        required: "Confirm Password is required",
                        validate: validateConfirmPassword
                    })} />
                    {errors.confirmPassword && <p>{errors.confirmPassword.message}</p>}
                </div>

                <div className='button-div'>
                    <button type="submit">
                        Submit
                    </button>
                </div>
            </form>
        </div>
    )
};

export default Form;
```

### Usando `useFormContext` 

`useFormContext` é um hook poderoso que permite compartilhar o contexto do formulário entre componentes aninhados, facilitando a reutilização de componentes de formulário.

Primeiro, configure o formulário principal utilizando o hook `useForm` do React Hook Form. Em seguida, envolva seus componentes de formulário aninhados com o componente `FormProvider` para compartilhar o contexto do formulário.

```tsx
import React from 'react';
import { useForm, FormProvider } from 'react-hook-form';

type FormValues = {
  firstName: string;
  lastName: string;
};

const App: React.FC = () => {
  const methods = useForm<FormValues>();

  const onSubmit = methods.handleSubmit((data) => {
    console.log(data);
  });

  return (
    <FormProvider {...methods}>
      <form onSubmit={onSubmit}>
        <FirstName />
        <LastName />
        <button type="submit">Submit</button>
      </form>
    </FormProvider>
  );
};

const FirstName: React.FC = () => {
  const { register } = useFormContext<FormValues>();
  return (
    <div>
      <label>First Name</label>
      <input {...register('firstName')} />
    </div>
  );
};

const LastName: React.FC = () => {
  const { register } = useFormContext<FormValues>();
  return (
    <div>
      <label>Last Name</label>
      <input {...register('lastName')} />
    </div>
  );
};

export default App;
```

### setError e setValue

Dois métodos úteis são `setError` e `setValue`, que permitem definir erros de validação manualmente e atualizar os valores dos campos de forma programática, respectivamente.

```tsx
import React from 'react';
import { useForm, SubmitHandler } from 'react-hook-form';

type FormValues = {
  cep: string;
  street: string;
  city: string;
  state: string;
};

const App: React.FC = () => {
  const { register, handleSubmit, setValue, setError } = useForm<FormValues>();

  const onSubmit: SubmitHandler<FormValues> = (data) => {
    console.log(data);
  };

  const fetchAddress = async (cep: string) => {
    try {
      const response = await fetch(`https://viacep.com.br/ws/${cep}/json/`);
      const data = await response.json();

      if (data.erro) {
        setError('cep', { type: 'manual', message: 'CEP inválido' });
      } else {
        setValue('street', data.logradouro);
        setValue('city', data.localidade);
        setValue('state', data.uf);
      }
    } catch (error) {
      setError('cep', { type: 'manual', message: 'Erro ao buscar CEP' });
    }
  };

  const handleCepBlur = (event: React.FocusEvent<HTMLInputElement>) => {
    const cep = event.target.value;
    if (cep) {
      fetchAddress(cep);
    }
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <div>
        <label>CEP</label>
        <input {...register('cep')} onBlur={handleCepBlur} />
      </div>
      <div>
        <label>Rua</label>
        <input {...register('street')} />
      </div>
      <div>
        <label>Cidade</label>
        <input {...register('city')} />
      </div>
      <div>
        <label>Estado</label>
        <input {...register('state')} />
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

export default App;
```

### Controller

O `Controller` é um componente que permite integrar componentes controlados (controlled components) de outras bibliotecas de UI com o `react-hook-form`.

```jsx
import React from 'react';
import { useForm, Controller } from 'react-hook-form';

const SimpleForm = () => {
  const { control, handleSubmit } = useForm();
  
  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <Controller
        name="firstName"
        control={control}
        defaultValue=""
        render={({ field }) => <input {...field} placeholder="First Name" />}
      />
      <input type="submit" />
    </form>
  );
};

export default SimpleForm;
```

#### Integração com Bibliotecas de UI

O `Controller` é especialmente útil quando se utiliza bibliotecas de componentes de UI que possuem seus próprios componentes controlados. Aqui está um exemplo com o Material-UI:

```jsx
import React from 'react';
import { useForm, Controller } from 'react-hook-form';
import TextField from '@mui/material/TextField';
import Button from '@mui/material/Button';

const MaterialUIForm = () => {
  const { control, handleSubmit } = useForm();
  
  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <Controller
        name="email"
        control={control}
        defaultValue=""
        render={({ field }) => <TextField {...field} label="Email" variant="outlined" />}
      />
      <Button type="submit" variant="contained" color="primary">Submit</Button>
    </form>
  );
};

export default MaterialUIForm;
```

#### Exemplo com Validação

Você pode adicionar validação facilmente ao usar o `Controller`. Aqui está um exemplo de como fazer isso:

```jsx
import React from 'react';
import { useForm, Controller } from 'react-hook-form';
import TextField from '@mui/material/TextField';
import Button from '@mui/material/Button';

const ValidationForm = () => {
  const { control, handleSubmit, formState: { errors } } = useForm();
  
  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <Controller
        name="email"
        control={control}
        defaultValue=""
        rules={{ required: 'Email is required', pattern: { value: /^\S+@\S+$/i, message: 'Invalid email address' } }}
        render={({ field }) => (
          <TextField
            {...field}
            label="Email"
            variant="outlined"
            error={!!errors.email}
            helperText={errors.email ? errors.email.message : ''}
          />
        )}
      />
      <Button type="submit" variant="contained" color="primary">Submit</Button>
    </form>
  );
};

export default ValidationForm;
```

### Usando Controladores Personalizados

Você pode criar seus próprios componentes controlados e integrá-los ao `react-hook-form` usando o `Controller`. Aqui está um exemplo:

```jsx
import React from 'react';
import { useForm, Controller } from 'react-hook-form';

const CustomInput = ({ value, onChange }) => (
  <input value={value} onChange={onChange} placeholder="Custom Input" />
);

const CustomControllerForm = () => {
  const { control, handleSubmit } = useForm();
  
  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <Controller
        name="customField"
        control={control}
        defaultValue=""
        render={({ field }) => <CustomInput {...field} />}
      />
      <input type="submit" />
    </form>
  );
};

export default CustomControllerForm;
```

#### Exemplo de Controladores Personalizados com React Input Mask

```typescript
import React from 'react';
import { useForm, Controller } from 'react-hook-form';
import InputMask from 'react-input-mask';

const PhoneNumberForm = () => {
  const { control, handleSubmit } = useForm();

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <Controller
        name="phoneNumber"
        control={control}
        defaultValue=""
        render={({ field }) => (
          <InputMask
            mask="(99) 99999-9999"
            value={field.value}
            onChange={field.onChange}
            onBlur={field.onBlur}
          >
            {(inputProps) => (
              <input
                {...inputProps}
                type="text"
                placeholder="(XX) XXXXX-XXXX"
              />
            )}
          </InputMask>
        )}
      />
      <input type="submit" value="Submit" />
    </form>
  );
};

export default PhoneNumberForm;
```

### Conclusão

O `Controller` do `react-hook-form` é uma ferramenta poderosa que permite integrar componentes controlados de outras bibliotecas com facilidade. Ele fornece uma interface consistente para manipular formulários e realizar validações, tornando a experiência de desenvolvimento mais eficiente e agradável.