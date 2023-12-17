# **Eventos no React**

Os eventos desempenham um papel fundamental no desenvolvimento de aplicativos React usando TypeScript, permitindo a resposta a diversas ações do usuário, como cliques e entradas de teclado. Vamos explorar alguns conceitos importantes relacionados aos eventos.

## **Tipagem de Eventos:**

Ao lidar com eventos, é crucial tipar corretamente para acessar as propriedades e valores específicos associados a cada tipo de evento. Utilize tipos genéricos, como MouseEvent, ChangeEvent, KeyboardEvent, etc. Veja exemplos:

   ```tsx
   function handleClick(event: React.MouseEvent<HTMLButtonElement>) {
     // Acesse propriedades do evento, como event.target
   }

   function handleInputChange(event: React.ChangeEvent<HTMLInputElement>) {
     // Acesse o valor do input com event.target.value
   }
   ```

## **Estado Inicial do Evento:**

Se desejar acessar o estado inicial do evento, como a posição do mouse no momento do clique, você pode armazená-lo em uma referência:

   ```tsx
   function handleClick(event: React.MouseEvent<HTMLButtonElement>) {
     const initialX = event.clientX;
     const initialY = event.clientY;
     // Use initialX e initialY conforme necessário
   }
   ```

## **Prevenção de Eventos Padrão:**

Para evitar comportamentos padrão, como a recarga da página em cliques de âncoras, use `event.preventDefault()`.

   ```tsx
   function handleLinkClick(event: React.MouseEvent<HTMLAnchorElement>) {
     event.preventDefault();
     // Agora você pode manipular a navegação ou fazer outras ações
   }
   ```

## **Passagem de Parâmetros para Event Handlers:**

   ```tsx
   function handleClick(id: number) {
     console.log(`Botão ${id} foi clicado.`);
   }

   <button onClick={() => handleClick(1)}>Botão 1</button>
   ```

## **Trabalhando com Eventos de Teclado:**

Eventos de teclado, como `onKeyDown`, são comuns em formulários. Certifique-se de tipar corretamente o evento.

   ```tsx
   function handleKeyPress(event: React.KeyboardEvent<HTMLInputElement>) {
     if (event.key === 'Enter') {
       // Realize a ação desejada quando a tecla Enter for pressionada
     }
   }
   ```


## Exemplo

```typescript
export function MeuBotao() {

    const handleClick = (event:React.MouseEvent) => {
        event.stopPropagation(); //Impede que o método se propague para os pais.
        alert(`Você clicou no ${event.currentTarget.id}.`);
    };

    return (
        <div>
            <button id='Botão' onClick={handleClick}>
        <div>
    )
}

```

Este exemplo ilustra como manipular eventos de clique em um botão React, garantindo que o tipo de evento seja tratado de forma adequada e que a propagação do evento seja controlada.