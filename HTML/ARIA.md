# ARIA (Accessible Rich Internet Applications)

O ARIA (Accessible Rich Internet Applications) é um conjunto de atributos que podem ser adicionados a elementos HTML para melhorar a acessibilidade de aplicativos da web. Este guia fornece orientações sobre como utilizar o ARIA para tornar suas aplicações mais acessíveis.

## Atributos Básicos do ARIA

### **`role` (função):**

   - Define a função do elemento, como `role="button"`, `role="navigation"`, etc.

     Exemplo:
     ```html
     <div role="button">Clique aqui</div>
     ```

### **`aria-label` (rótulo):**

   - Fornece um rótulo textual para um elemento que não possui texto visível.

     Exemplo:
     ```html
     <img src="icon.png" aria-label="Ícone de Menu">
     ```

### **`aria-labelledby` (rótulo referente):**

   - Associa um elemento a um rótulo fornecido por `id`.

     Exemplo:
     ```html
     <div id="titulo">Título Importante</div>
     <div aria-labelledby="titulo">Conteúdo</div>
     ```

### **`aria-describedby` (descrição referente):**

   - Associa um elemento a uma descrição fornecida por `id`.

     Exemplo:
     ```html
     <input type="password" aria-describedby="instrucoes">
     <div id="instrucoes">Digite sua senha segura.</div>
     ```

## Complementando Elementos Semânticos

### **`aria-hidden` (ocultar):**

   - Indica que um elemento deve ser ocultado de leitores de tela e não faça parte da acessibilidade.

     Exemplo:
     ```html
     <div aria-hidden="true">Conteúdo não acessível</div>
     ```

### **`aria-expanded` (expandido):**

   - Informa o estado "expandido" ou "recolhido" de um elemento, como um painel de acordeão.

     Exemplo:
     ```html
     <button aria-expanded="true">Mostrar Detalhes</button>
     ```

### **`aria-checked` (marcado):**

   - Indica o estado "marcado" ou "não marcado" de elementos como caixas de seleção.

     Exemplo:
     ```html
     <input type="checkbox" aria-checked="true"> Opção Selecionada
     ```

## Navegação e Controles

### **`aria-haspopup` (possui menu suspenso):**

   - Indica se um elemento gera um menu suspenso.

     Exemplo:
     ```html
     <button aria-haspopup="true">Menu</button>
     ```

### **`aria-controls` (controla):**

   - Associa um elemento a outro que ele controla, como um botão de abertura de modal.

     Exemplo:
     ```html
     <button id="abrirModal" aria-controls="conteudoModal">Abrir Modal</button>
     <div id="conteudoModal">Conteúdo do Modal</div>
     ```

### **`aria-pressed` (pressionado):**

- Indica se um botão ou alternância está pressionado.

    Exemplo:
    ```html
    <button aria-pressed="false">Botão Não Pressionado</button>
    ```

### Progresso e Status

### **`aria-progressbar` (barra de progresso):**

- Define uma barra de progresso com marcador.

    Exemplo:
    ```html
    <div role="progressbar" aria-valuemin="0" aria-valuemax="100" aria-valuenow="50">50%</div>
    ```

### **`aria-valuemax` (valor máximo):**

- Define o valor máximo para elementos com valores, como barras de progresso.

    Exemplo:
    ```html
    <div role="slider" aria-valuemax="100">Deslize para 100</div>
    ```

### **`aria-live` (conteúdo ao vivo):**

- Indica que uma região contém conteúdo dinâmico que deve ser anunciado por leitores de tela.

    Exemplo:
    ```html
    <div aria-live="polite">Atualizações ao vivo aparecerão aqui</div>
    ```

## Diálogos e Modais

### **`aria-modal` (modal):**

- Indica que um elemento representa um diálogo modal.

    Exemplo:
    ```html
    <div aria-modal="true">Conteúdo do Diálogo Modal</div>
    ```

### **`aria-labelledby` (rótulo referente ao diálogo):**

- Associa um diálogo modal a seu rótulo.

    Exemplo:
    ```html
    <div id="tituloModal">Título do Modal</div>
    <div aria-labelledby="tituloModal">Conteúdo do Modal</div>
    ```

### **`aria-describedby` (descrição referente ao diálogo):**

- Associa um diálogo modal a sua descrição.

    Exemplo:
    ```html
    <div id="instrucoesModal">Instruções Importantes</div>
    <div aria-describedby="instrucoesModal">Conteúdo do Modal</div>
    ```

Lembre-se de que o uso correto do ARIA é essencial. Ele não deve substituir a semântica HTML adequada, mas sim complementá-la para melhorar a acessibilidade. Certifique-se de entender o contexto de uso e seguir as diretrizes de ARIA para criar aplicativos web mais inclusivos.