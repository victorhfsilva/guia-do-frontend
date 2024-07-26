# Formulários Dinâmicos usando Zod e React Hook Form

### Introdução

Formulários dinâmicos são aqueles que permitem aos usuários adicionar ou remover campos conforme necessário. Um exemplo comum é um formulário para adicionar múltiplos endereços de e-mail. 

### Instalação

Primeiro, você precisa instalar as bibliotecas necessárias:

```bash
npm install zod react-hook-form @hookform/resolvers
```

### Configurando o Schema com Zod

Vamos definir um schema usando Zod para validar que cada e-mail é uma string válida e não está vazia:

```typescript
import { z } from 'zod';

const EmailSchema = z.object({
  emails: z.array(z.object({
    email: z.string().email("Invalid email address").nonempty("Email is required")
  }))
});

type EmailFormData = z.infer<typeof EmailSchema>;
```

### Configurando o Formulário com React Hook Form

Vamos configurar o formulário utilizando React Hook Form e o hook `useFieldArray` para gerenciar os campos dinâmicos:

```typescript
import React from 'react';
import { useForm, useFieldArray, Controller } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import { z } from 'zod';

const EmailSchema = z.object({
  emails: z.array(z.object({
    email: z.string().email("Invalid email address").nonempty("Email is required")
  }))
});

type EmailFormData = z.infer<typeof EmailSchema>;

const DynamicForm: React.FC = () => {
  const { control, register, handleSubmit, formState: { errors } } = useForm<EmailFormData>({
    resolver: zodResolver(EmailSchema),
  });

  const { fields, append, remove } = useFieldArray({
    control,
    name: "emails"
  });

  const onSubmit = (data: EmailFormData) => {
    console.log("Form Data:", data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      {fields.map((field, index) => (
        <div key={field.id}>
          <label htmlFor={`emails.${index}.email`}>Email {index + 1}</label>
          <input
            id={`emails.${index}.email`}
            {...register(`emails.${index}.email`)}
          />
          {errors.emails && errors.emails[index] && (
            <span>{errors.emails?.[index]?.email?.message}</span>
          )}
          <button type="button" onClick={() => remove(index)}>Remove</button>
        </div>
      ))}
      <button type="button" onClick={() => append({ email: "" })}>Add Email</button>
      <button type="submit">Submit</button>
    </form>
  );
};

export default DynamicForm;
```

### Explicação dos Componentes

1. **Schema com Zod**:
   - `z.array(z.object({ ... }))` define um array de objetos, onde cada objeto representa um campo de e-mail.
   - `z.string().email("Invalid email address").nonempty("Email is required")` valida que o campo de e-mail é uma string não vazia e é um endereço de e-mail válido.

2. **Formulário com React Hook Form**:
   - `useForm` cria hooks de formulário, onde `resolver: zodResolver(EmailSchema)` é usado para integrar a validação do Zod.
   - `useFieldArray` é usado para gerenciar campos dinâmicos no formulário.
   - `register` conecta campos de formulário à lógica do React Hook Form.
   - `handleSubmit` gerencia o envio do formulário e chama `onSubmit` se a validação passar.
   - `fields` contém os campos dinâmicos atuais.
   - `append` adiciona um novo campo de e-mail.
   - `remove` remove um campo de e-mail existente.

3. **Renderizando os Campos Dinâmicos**:
   - Mapeamos sobre os `fields` e renderizamos um input para cada e-mail, incluindo um botão para remover o campo.
   - O botão "Add Email" adiciona um novo campo de e-mail ao formulário.
