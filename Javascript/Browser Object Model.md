# Browser Object Model (BOM) 
O Browser Object Model (BOM) não possui padrões oficiais, mas os navegadores modernos implementaram métodos e propriedades semelhantes para interatividade em JavaScript, geralmente referidos como métodos e propriedades do BOM.

## **Objeto Window:**

- O objeto `window` é suportado por todos os navegadores e representa a janela do navegador.
- Todos os objetos, funções e variáveis globais em JavaScript automaticamente se tornam membros do objeto `window`.
- Variáveis globais são propriedades do objeto `window`.
- Funções globais são métodos do objeto `window`.

### Exemplo:
```javascript
let minhaVariavel = "Olá, Mundo!";
console.log(window.minhaVariavel); // Acesse variáveis globais usando window.
```

## Variáveis Globais:

### Window Location
- **Descrição**: Fornece informações sobre a URL atual e permite a manipulação da mesma.
- **Exemplo**: `const currentURL = window.location.href;`
- **Mais Informações**: [Window Location: W3Schools](https://www.w3schools.com/jsref/obj_location.asp)

### Window Document
- **Descrição**: Referência ao objeto `document`, que representa o documento HTML atual.

### Window Navigator
- **Descrição**: Fornece informações sobre o navegador do usuário, como nome e versão.
- **Exemplo**: `const browserName = window.navigator.userAgent;`
- **Mais Informações**: [Window Navigator: W3Schools](https://www.w3schools.com/jsref/obj_navigator.asp)

### Window LocalStorage e Window SessionStorage
- **Descrição**: Permite armazenar dados no navegador do usuário.
- **Exemplo**: 
  ```javascript
  window.localStorage.setItem('key', 'value');
  const storedValue = window.localStorage.getItem('key');
  ```

### Window History
- **Descrição:** O objeto history contém o histórico de navegação da sessão.
- **Exemplo:** 
```javascript
window.history.back(); // Navega para a página anterior no histórico
```
- **Mais informações:** [Window History: W3Schools](https://www.w3schools.com/jsref/obj_history.asp)

### Window Screen
- **Descrição:** Fornece informações sobre a tela do dispositivo.
- **Exemplo:**
```javascript
console.log(window.screen.width); // Largura da tela do dispositivo
```
- **Mais Informações:** [Window Screen: W3Schools](https://www.w3schools.com/jsref/obj_screen.asp)

### Window Console
- **Descrição:** O objeto console fornece métodos para interagir com o console de desenvolvedor do navegador.
- **Exemplo:**

```javascript
console.log("Mensagem de log");
```
- **Mais Informações:** [Window Console: W3Schools](https://www.w3schools.com/jsref/obj_console.asp)

## Métodos Globais:

### `window.alert(message)`
- **Descrição**: Exibe uma caixa de diálogo de alerta com a mensagem especificada.
- **Exemplo**: `window.alert('Isso é um alerta!');`

### `window.confirm(message)`
- **Descrição**: Exibe uma caixa de diálogo de confirmação com a mensagem especificada e retorna `true` se o usuário clicar em "OK" e `false` se clicar em "Cancelar".
- **Exemplo**: `const userConfirmed = window.confirm('Você tem certeza?');`

### `window.prompt(message, defaultValue)`
- **Descrição**: Exibe uma caixa de diálogo de entrada com a mensagem e um valor padrão especificados, retornando o valor inserido pelo usuário.
- **Exemplo**: `const userInput = window.prompt('Digite algo:', 'Padrão');`

### `window.open(url, name, features)`
- **Descrição**: Abre uma nova janela do navegador com a URL especificada e opções de janela.
- **Exemplo**: `window.open('https://www.example.com', 'minhaJanela', 'width=500,height=300');`

### `window.close()`
- **Descrição**: Fecha a janela atual (geralmente usada para janelas abertas com `window.open`).

### `window.setTimeout(callback, delay)`
- **Descrição**: Chama a função de retorno especificada após um atraso em milissegundos.
- **Exemplo**: `window.setTimeout(() => console.log('Executado após 2 segundos'), 2000);`

### `window.clearTimeout(timeoutID)`
- **Descrição**: Cancela um atraso definido anteriormente com `setTimeout`.

### `window.setInterval(callback, interval)`
- **Descrição**: Chama a função de retorno especificada em intervalos regulares.
- **Exemplo**: `window.setInterval(() => console.log('A cada 5 segundos'), 5000);`

### `window.clearInterval(intervalID)`
- **Descrição**: Cancela a execução de uma função definida anteriormente com `setInterval`.

Esses são apenas alguns dos recursos disponíveis no objeto `window`. Ele representa o ambiente de execução global em um navegador da web e fornece acesso a uma variedade de informações e funcionalidades relacionadas ao navegador e à janela atual. É importante usá-lo com responsabilidade e considerar a compatibilidade do navegador ao trabalhar com essas variáveis e métodos globais.
