# **Formulários Controlados no React**

Formulários controlados no React referem-se a um padrão em que os dados do formulário são manipulados pelo estado do React. Aqui está um guia sobre como usar formulários controlados:

## **Estado Inicial:**

   Comece definindo um estado para os valores dos campos do formulário.

   ```jsx
   import React, { useState } from 'react';

   const MyForm = () => {
     const [formData, setFormData] = useState({
       username: '',
       email: '',
       password: '',
     });

     // ... restante do componente
   };
   ```

## **Entradas Controladas:**

   Associe cada campo de entrada a um valor no estado e forneça uma função para atualizar esse valor.

   ```jsx
   const MyForm = () => {
     const [formData, setFormData] = useState({
       username: '',
       email: '',
       password: '',
     });

     const handleInputChange = (e) => {
       const { name, value } = e.target;
       setFormData({
         ...formData,
         [name]: value,
       });
     };

     return (
       <form>
         <label>
           Username:
           <input
             type="text"
             name="username"
             value={formData.username}
             onChange={handleInputChange}
           />
         </label>

         <label>
           Email:
           <input
             type="email"
             name="email"
             value={formData.email}
             onChange={handleInputChange}
           />
         </label>

         <label>
           Password:
           <input
             type="password"
             name="password"
             value={formData.password}
             onChange={handleInputChange}
           />
         </label>
       </form>
     );
   };
   ```

## **Envio do Formulário:**

   Manipule o evento `onSubmit` do formulário para lidar com os dados quando o formulário for enviado.

   ```jsx
   const MyForm = () => {
     const [formData, setFormData] = useState({
       username: '',
       email: '',
       password: '',
     });

     const handleInputChange = (e) => {
       const { name, value } = e.target;
       setFormData({
         ...formData,
         [name]: value,
       });
     };

     const handleSubmit = (e) => {
       e.preventDefault();
       // Faça algo com os dados, por exemplo, envie para um servidor
       console.log(formData);
     };

     return (
       <form onSubmit={handleSubmit}>
         {/* ... campos de entrada */}
         <button type="submit">Submit</button>
       </form>
     );
   };
   ```

## **Validação de Entrada:**

   Adicione lógica de validação conforme necessário, por exemplo, para garantir que os campos obrigatórios sejam preenchidos.

   ```jsx
   const MyForm = () => {
     // ...

     const handleSubmit = (e) => {
       e.preventDefault();
       
       if (!formData.username || !formData.email || !formData.password) {
         alert('Preencha todos os campos obrigatórios.');
         return;
       }

       // Faça algo com os dados
       console.log(formData);
     };

     // ...
   };
   ```

## **Limpar Formulário:**

   Adicione um botão para limpar os campos do formulário quando necessário.

   ```jsx
   const MyForm = () => {
     // ...

     const handleClear = () => {
       setFormData({
         username: '',
         email: '',
         password: '',
       });
     };

     return (
       <form onSubmit={handleSubmit}>
         {/* ... campos de entrada */}
         <button type="submit">Submit</button>
         <button type="button" onClick={handleClear}>Clear</button>
       </form>
     );
   };
   ```
