# **Formulários Não Controlados no React**

Formulários não controlados referem-se a um padrão em que os dados do formulário não são gerenciados pelo estado do React, mas sim pelo DOM. 

## **Ref para Elementos:**

   Utilize a API de ref do React para obter referências aos elementos do formulário.

   ```jsx
   import React, { useRef } from 'react';

   const MyForm = () => {
     const usernameRef = useRef();
     const emailRef = useRef();
     const passwordRef = useRef();

     // ... restante do componente
   };
   ```

   Ou, em tsx:

   ```tsx
    import React, { useRef } from 'react';

    const MyForm: React.FC = () => {
      const usernameRef = useRef<HTMLInputElement>(null);
      const emailRef = useRef<HTMLInputElement>(null);
      const passwordRef = useRef<HTMLInputElement>(null);

      // ... restante do componente
    };

    export default MyForm;
   ```

## **Captura de Dados:**

   Obtenha os valores dos campos diretamente a partir das referências quando necessário.

   ```jsx
   const MyForm = () => {
     const usernameRef = useRef();
     const emailRef = useRef();
     const passwordRef = useRef();

     const handleSubmit = (e) => {
       e.preventDefault();

       const username = usernameRef.current.value;
       const email = emailRef.current.value;
       const password = passwordRef.current.value;

       // Faça algo com os dados
       console.log(username, email, password);
     };

     // ... restante do componente
   };
   ```

## **Elementos do Formulário:**

   Associe as referências aos elementos do formulário.

   ```jsx
   const MyForm = () => {
     const usernameRef = useRef();
     const emailRef = useRef();
     const passwordRef = useRef();

     const handleSubmit = (e) => {
       e.preventDefault();

       const username = usernameRef.current.value;
       const email = emailRef.current.value;
       const password = passwordRef.current.value;

       // Faça algo com os dados
       console.log(username, email, password);
     };

     return (
       <form onSubmit={handleSubmit}>
         <label>
           Username:
           <input ref={usernameRef} type="text" />
         </label>

         <label>
           Email:
           <input ref={emailRef} type="email" />
         </label>

         <label>
           Password:
           <input ref={passwordRef} type="password" />
         </label>

         <button type="submit">Submit</button>
       </form>
     );
   };
   ```

   Ou, em tsx:

   ```tsx
    import React, { useRef, FormEvent } from 'react';

    const MyForm: React.FC = () => {
      const usernameRef = useRef<HTMLInputElement>(null);
      const emailRef = useRef<HTMLInputElement>(null);
      const passwordRef = useRef<HTMLInputElement>(null);

      const handleSubmit = (e: FormEvent) => {
        e.preventDefault();

        const username = usernameRef.current?.value;
        const email = emailRef.current?.value;
        const password = passwordRef.current?.value;

        // Faça algo com os dados
        console.log(username, email, password);
      };

      return (
        <form onSubmit={handleSubmit}>
          <label>
            Username:
            <input ref={usernameRef} type="text" />
          </label>

          <label>
            Email:
            <input ref={emailRef} type="email" />
          </label>

          <label>
            Password:
            <input ref={passwordRef} type="password" />
          </label>

          <button type="submit">Submit</button>
        </form>
      );
    };

    export default MyForm;

   ```

## **Limpar Formulário:**

   Para limpar o formulário, você pode definir os valores diretamente nos elementos do DOM através das referências.

   ```jsx
   const MyForm = () => {
     const usernameRef = useRef();
     const emailRef = useRef();
     const passwordRef = useRef();

     const handleSubmit = (e) => {
       e.preventDefault();

       const username = usernameRef.current.value;
       const email = emailRef.current.value;
       const password = passwordRef.current.value;

       // Faça algo com os dados
       console.log(username, email, password);

       // Limpe o formulário
       usernameRef.current.value = '';
       emailRef.current.value = '';
       passwordRef.current.value = '';
     };

     // ... restante do componente
   };
   ```

## **Uso com Componentes Controlados:**

   Em alguns casos, você pode misturar abordagens controladas e não controladas.

   ```jsx
   const MyForm = () => {
     const usernameRef = useRef();
     const [email, setEmail] = useState('');

     const handleSubmit = (e) => {
       e.preventDefault();

       const username = usernameRef.current.value;

       // Faça algo com os dados
       console.log(username, email);
     };

     return (
       <form onSubmit={handleSubmit}>
         <label>
           Username:
           <input ref={usernameRef} type="text" />
         </label>

         <label>
           Email:
           <input
             type="email"
             value={email}
             onChange={(e) => setEmail(e.target.value)}
           />
         </label>

         <button type="submit">Submit</button>
       </form>
     );
   };
   ```

Formulários não controlados podem ser úteis em situações específicas, mas em geral, a abordagem controlada com estado do React é mais poderosa e mantém um controle mais preciso sobre o estado do aplicativo.