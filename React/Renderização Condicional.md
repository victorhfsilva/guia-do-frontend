# **Renderização Condicional em React**

Em React, a renderização condicional permite exibir componentes com base em condições específicas. Existem várias maneiras de alcançar esse objetivo.

## **Declaração if:**
   
   - **Uso:** O operador if do JavaScript é empregado para decidir qual componente renderizar.
   
   - **Exemplo:**
   
     ```jsx
     function GolPerdido() {
       return <h1>PERDIDO!</h1>;
     }

     function GolFeito() {
       return <h1>Gol!</h1>;
     }

     function Gol(props) {
       const foiGol = props.foiGol;
       if (foiGol) {
         return <GolFeito />;
       }
       return <GolPerdido />;
     }

     const root = ReactDOM.createRoot(document.getElementById('root'));
     root.render(<Gol foiGol={false} />);
     ```

## **Operador lógico &&:**
   
   - Utiliza-se o operador && para renderização condicional em JSX.
   
   - **Exemplo: Verificando Carros na Garagem**
   
     ```jsx
     function Garagem(props) {
       const carros = props.carros;
       return (
         <>
           <h1>Garagem</h1>
           {carros.length > 0 && (
             <h2>
               Você tem {carros.length} carros na sua garagem.
             </h2>
           )}
         </>
       );
     }

     const carros = ['Ford', 'BMW', 'Audi'];
     const root = ReactDOM.createRoot(document.getElementById('root'));
     root.render(<Garagem carros={carros} />);
     ```

     Ou, em tsx:

     ```tsx
      import React from 'react';
      import ReactDOM from 'react-dom';

      interface GaragemProps {
        carros: string[];
      }

      function Garagem(props: GaragemProps) {
        const { carros } = props;

        return (
          <>
            <h1>Garagem</h1>
            {carros.length > 0 && (
              <h2>
                Você tem {carros.length} carros na sua garagem.
              </h2>
            )}
          </>
        );
      }

      const carros: string[] = ['Ford', 'BMW', 'Audi'];
      const root = ReactDOM.createRoot(document.getElementById('root')!);
      root.render(<Garagem carros={carros} />);

     ```

## **Operador Ternário:**
   
   - Outra abordagem é usar um operador ternário para renderizar elementos condicionalmente.
   
   - **Exemplo: Alternando entre Componentes Gol**
   
     ```jsx
     function Gol(props) {
       const foiGol = props.foiGol;
       return (
         <>
           {foiGol ? <GolFeito /> : <GolPerdido />}
         </>
       );
     }

     const root = ReactDOM.createRoot(document.getElementById('root'));
     root.render(<Gol foiGol={false} />);
     ```
