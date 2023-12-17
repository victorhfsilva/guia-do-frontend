# **Formulários em React**

## **Introdução aos Formulários em React:**

Em React, adicionar um formulário é semelhante a adicionar qualquer outro elemento. No entanto, o controle do formulário é manipulado de maneira mais eficiente.

## **Escrevendo um Formulário Básico:**

     ```jsx
     function MeuFormulario() {
       return (
         <form>
           <label>Informe seu nome:
             <input type="text" />
           </label>
         </form>
       )
     }

     const root = ReactDOM.createRoot(document.getElementById('root'));
     root.render(<MeuFormulario />);
     ```

## **Manipulação de Formulários em React:**
   
   - **Controle pelos Componentes:** Em React, o controle dos dados do formulário é tratado pelos próprios componentes, permitindo armazenar todos os dados no estado do componente.

   - **Exemplo: Utilizando o Hook useState**
     ```jsx
     import { useState } from 'react';
     import ReactDOM from 'react-dom/client';

     function MeuFormulario() {
       const [nome, setNome] = useState("");

       return (
         <form>
           <label>Informe seu nome:
             <input
               type="text"
               value={nome}
               onChange={(e) => setNome(e.target.value)}
             />
           </label>
         </form>
       )
     }

     const root = ReactDOM.createRoot(document.getElementById('root'));
     root.render(<MeuFormulario />);
     ```
     
     Ou, em tsx: 

     ```tsx
        import React, { useState, ChangeEvent } from 'react';
        import ReactDOM from 'react-dom';

        function MeuFormulario() {
        const [nome, setNome] = useState<string>("");

        return (
            <form>
            <label>Informe seu nome:
                <input
                type="text"
                value={nome}
                onChange={(e: ChangeEvent<HTMLInputElement>) => setNome(e.target.value)}
                />
            </label>
            </form>
        );
        }

        const root = ReactDOM.createRoot(document.getElementById('root')!);
        root.render(<MeuFormulario />);

     ```

     - Agora, o estado (`nome`) é controlado pelo componente, e a função `onChange` atualiza o estado conforme o valor é alterado.

## **Enviando Formulários e Prevenindo o Comportamento Padrão:**

   - **Prevenção do Comportamento Padrão:** Para evitar o recarregamento da página ao enviar o formulário, é crucial utilizar `event.preventDefault()` no manipulador de eventos `onSubmit`.

   - **Exemplo: Adicionando um Botão de Envio**

     ```jsx
     import { useState } from 'react';
     import ReactDOM from 'react-dom/client';

     function MeuFormulario() {
       const [nome, setNome] = useState("");

       const handleSubmit = (event) => {
         event.preventDefault();
         alert(`O nome que você digitou foi: ${nome}`);
       }

       return (
         <form onSubmit={handleSubmit}>
           <label>Informe seu nome:
             <input
               type="text"
               value={nome}
               onChange={(e) => setNome(e.target.value)}
             />
           </label>
           <input type="submit" />
         </form>
       )
     }

     const root = ReactDOM.createRoot(document.getElementById('root'));
     root.render(<MeuFormulario />);
     ```

     Ou, em tsx:

     ```tsx
        import React, { useState, ChangeEvent, FormEvent } from 'react';
        import ReactDOM from 'react-dom';

        function MeuFormulario() {
        const [nome, setNome] = useState<string>("");

        const handleSubmit = (event: FormEvent<HTMLFormElement>) => {
            event.preventDefault();
            alert(`O nome que você digitou foi: ${nome}`);
        }

        return (
            <form onSubmit={handleSubmit}>
            <label>Informe seu nome:
                <input
                type="text"
                value={nome}
                onChange={(e: ChangeEvent<HTMLInputElement>) => setNome(e.target.value)}
                />
            </label>
            <input type="submit" />
            </form>
        );
        }

        const root = ReactDOM.createRoot(document.getElementById('root')!);
        root.render(<MeuFormulario />);
     ```

## **Manipulação de Múltiplos Campos:**

   - **Utilizando o Hook useState para Vários Campos:** Ao lidar com vários campos, use um objeto no estado inicial e atualize-o de acordo com o campo correspondente.

   - **Exemplo: Dois Campos de Entrada**
     ```jsx
     import { useState } from 'react';
     import ReactDOM from 'react-dom/client';

     function MeuFormulario() {
       const [inputs, setInputs] = useState({});

       const handleChange = (event) => {
         const name = event.target.name;
         const value = event.target.value;
         setInputs(values => ({...values, [name]: value}));
       }

       const handleSubmit = (event) => {
         event.preventDefault();
         alert(JSON.stringify(inputs));
       }

       return (
         <form onSubmit={handleSubmit}>
           <label>Informe seu nome:
             <input
               type="text"
               name="username"
               value={inputs.username || ""}
               onChange={handleChange}
             />
           </label>
           <label>Informe sua idade:
             <input
               type="number"
               name="age"
               value={inputs.age || ""}
               onChange={handleChange}
             />
           </label>
           <input type="submit" />
         </form>
       )
     }

     const root = ReactDOM.createRoot(document.getElementById('root'));
     root.render(<MeuFormulario />);
     ```

     Ou, em tsx:

     ```tsx
        import React, { useState, ChangeEvent, FormEvent } from 'react';
        import ReactDOM from 'react-dom';

        interface FormInputs {
            username?: string;
            age?: string;
        }

        function MeuFormulario() {
        const [inputs, setInputs] = useState<FormInputs>({});

        const handleChange = (event: ChangeEvent<HTMLInputElement>) => {
            const name = event.target.name;
            const value = event.target.value;
            setInputs(values => ({ ...values, [name]: value }));
        }

        const handleSubmit = (event: FormEvent<HTMLFormElement>) => {
            event.preventDefault();
            alert(JSON.stringify(inputs));
        }

        return (
            <form onSubmit={handleSubmit}>
            <label>Informe seu nome:
                <input
                type="text"
                name="username"
                value={inputs.username || ""}
                onChange={handleChange}
                />
            </label>
            <label>Informe sua idade:
                <input
                type="number"
                name="age"
                value={inputs.age || ""}
                onChange={handleChange}
                />
            </label>
            <input type="submit" />
            </form>
        );
        }

        const root = ReactDOM.createRoot(document.getElementById('root')!);
        root.render(<MeuFormulario />);
     ```

## **Trabalhando com Textarea e Select em React:**

   - **Textarea:** Em React, o valor de um `<textarea>` é gerenciado com o atributo `value` e o Hook `useState`.
   
   - **Select:** A manipulação de uma caixa de seleção (`<select>`) também é realizada usando o atributo `value` e o Hook `useState`.

   - **Exemplo: Textarea e Select Simples**
     ```jsx
     import { useState } from 'react';
     import ReactDOM from 'react-dom/client';

     function MeuFormulario() {
       const [textarea, setTextarea] = useState(
         "O conteúdo de um textarea vai no atributo 'value'"
       );
       const [myCar, setMyCar] = useState("Volvo");

       const handleTextareaChange = (event) => {
         setTextarea(event.target.value);
       }

       const handleSelectChange = (event) => {
         setMyCar(event.target.value);
       }

       return (
         <form>
           <textarea value={textarea} onChange={handleTextareaChange} />
           <select value={myCar} onChange={handleSelectChange}>
             <option value="Ford">Ford</option>
             <option value="Volvo">Volvo</option>
             <option value="Fiat">Fiat</option>
           </select>
         </form>
       )
     }

     const root = ReactDOM.createRoot(document.getElementById('root'));
     root.render(<MeuFormulario />);
     ```

     Ou, em tsx:

     ```tsx
        import React, { useState, ChangeEvent } from 'react';
        import ReactDOM from 'react-dom';

        function MeuFormulario() {
        const [textarea, setTextarea] = useState(
            "O conteúdo de um textarea vai no atributo 'value'"
        );
        const [myCar, setMyCar] = useState<string>("Volvo");

        const handleTextareaChange = (event: ChangeEvent<HTMLTextAreaElement>) => {
            setTextarea(event.target.value);
        }

        const handleSelectChange = (event: ChangeEvent<HTMLSelectElement>) => {
            setMyCar(event.target.value);
        }

        return (
            <form>
            <textarea value={textarea} onChange={handleTextareaChange} />
            <select value={myCar} onChange={handleSelectChange}>
                <option value="Ford">Ford</option>
                <option value="Volvo">Volvo</option>
                <option value="Fiat">Fiat</option>
            </select>
            </form>
        );
        }

        const root = ReactDOM.createRoot(document.getElementById('root')!);
        root.render(<MeuFormulario />);

     ```
