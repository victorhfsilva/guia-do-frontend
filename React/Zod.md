# Zod: Validação de Schemas

Zod é uma biblioteca TypeScript-first de validação de schemas e parsing. Ao contrário de outras bibliotecas de validação, como Joi ou Yup, Zod foi projetado com TypeScript em mente, oferecendo uma ótima integração com tipos e permitindo validações seguras em tempo de compilação.

### Instalação

Primeiro, você precisa instalar o Zod e as bibliotecas que vamos usar no exemplo:

```bash
npm install zod react-hook-form @hookform/resolvers
```

### Conceitos Básicos do Zod

Zod permite definir schemas para diferentes tipos de dados e validar objetos JavaScript contra esses schemas. Aqui estão alguns exemplos básicos:

```typescript
import { z } from 'zod';

const UserSchema = z.object({
  name: z.string(),
  age: z.number().min(18),
  email: z.string().email(),
});

// Validando um objeto
const result = UserSchema.safeParse({
  name: "John Doe",
  age: 25,
  email: "john.doe@example.com"
});

if (result.success) {
  console.log("Valid object:", result.data);
} else {
  console.error("Validation errors:", result.error.errors);
}
```

### Integrando Zod com React Hook Form

React Hook Form (RHF) é uma biblioteca para lidar com formulários em React, que se integra muito bem com Zod para validação de formulários. Vamos criar um exemplo de formulário usando React, RHF e Zod.

#### Configurando o Formulário

```typescript
import React from 'react';
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import { z } from 'zod';

const UserSchema = z.object({
  name: z.string().nonempty("Name is required"),
  age: z.number().min(18, "You must be at least 18 years old"),
  email: z.string().email("Invalid email address"),
});

type UserFormData = z.infer<typeof UserSchema>;

const UserForm: React.FC = () => {
  const { register, handleSubmit, formState: { errors } } = useForm<UserFormData>({
    resolver: zodResolver(UserSchema),
  });

  const onSubmit = (data: UserFormData) => {
    console.log("Form Data:", data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <div>
        <label htmlFor="name">Name</label>
        <input id="name" {...register('name')} />
        {errors.name && <span>{errors.name.message}</span>}
      </div>

      <div>
        <label htmlFor="age">Age</label>
        <input id="age" type="number" {...register('age', { valueAsNumber: true })} />
        {errors.age && <span>{errors.age.message}</span>}
      </div>

      <div>
        <label htmlFor="email">Email</label>
        <input id="email" {...register('email')} />
        {errors.email && <span>{errors.email.message}</span>}
      </div>

      <button type="submit">Submit</button>
    </form>
  );
};

export default UserForm;
```

#### Explicação dos Componentes

1. **Definindo o Schema com Zod**:
   - `z.object({...})` define um objeto com propriedades especificadas.
   - `z.string().nonempty("Message")` define uma string que não pode ser vazia.
   - `z.number().min(18, "Message")` define um número com um valor mínimo.
   - `z.string().email("Message")` valida um endereço de e-mail.

2. **Integrando Zod com React Hook Form**:
   - `useForm` é usado para criar hooks de formulário, onde passamos `resolver: zodResolver(UserSchema)` para integrar a validação do Zod.
   - `register` é usado para conectar campos de formulário à lógica do React Hook Form.
   - `handleSubmit` gerencia o envio do formulário e chama `onSubmit` se a validação passar.
   - `formState: { errors }` é usado para acessar erros de validação e exibi-los.

### Utilizando o Método `transform`

O método `transform` do Zod permite transformar valores durante a validação. Isso é útil quando você precisa formatar ou ajustar os dados de entrada antes de utilizá-los no seu aplicativo. Vamos explorar como usar `transform` com Zod em um contexto de um formulário em React.

#### Exemplo

Primeiro, definimos o schema utilizando o método `transform`:

```typescript
import { z } from 'zod';

const UserSchema = z.object({
  name: z.string().nonempty("Name is required").transform((val) => val.toUpperCase()),
  age: z.number().min(18, "You must be at least 18 years old"),
  email: z.string().email("Invalid email address"),
});

type UserFormData = z.infer<typeof UserSchema>;
```

### Utilizando refine`

O método `refine` do Zod permite adicionar validações customizadas que não são cobertas pelos métodos de validação padrão. Isso é útil quando você precisa de validações mais complexas ou específicas.

#### Exemplo

```typescript
import { z } from 'zod';

const PasswordSchema = z.object({
  password: z.string().min(6, "Password must be at least 6 characters long"),
  confirmPassword: z.string().min(6, "Confirm Password must be at least 6 characters long"),
}).refine(data => data.password === data.confirmPassword, {
  message: "Passwords don't match",
  path: ["confirmPassword"],
});

type PasswordFormData = z.infer<typeof PasswordSchema>;
```

### Utilizando o `superRefine`

O método `superRefine` do Zod é uma versão avançada de `refine`, permitindo validações complexas e interdependentes em um nível mais detalhado. Ele oferece maior controle sobre como os erros são manipulados, permitindo que você adicione múltiplos erros e especifique caminhos personalizados para cada um.

#### Exemplo

```typescript
import { z } from 'zod';

const PasswordSchema = z.object({
  password: z.string().min(6, "Password must be at least 6 characters long"),
  confirmPassword: z.string().min(6, "Confirm Password must be at least 6 characters long"),
}).superRefine((data, ctx) => {
  if (data.password !== data.confirmPassword) {
    ctx.addIssue({
      code: z.ZodIssueCode.custom,
      message: "Passwords don't match",
      path: ["confirmPassword"],
    });
  }

  if (!/[A-Z]/.test(data.password)) {
    ctx.addIssue({
      code: z.ZodIssueCode.custom,
      message: "Password must contain at least one uppercase letter",
      path: ["password"],
    });
  }

  if (!/[0-9]/.test(data.password)) {
    ctx.addIssue({
      code: z.ZodIssueCode.custom,
      message: "Password must contain at least one number",
      path: ["password"],
    });
  }
});

type PasswordFormData = z.infer<typeof PasswordSchema>;
```