# Eventos Globais para Captura de Erros Não Tratados

Ao utilizar os eventos globais `window.onerror` no navegador e `process.on('uncaughtException')` no Node.js, é possível capturar erros não tratados globalmente. Isso pode ser útil para registrar informações sobre erros que não foram capturados por manipuladores específicos.

## No Navegador:

```javascript
// Configurando o evento window.onerror para capturar erros globais no navegador
window.onerror = function(mensagem, origem, numeroLinha, numeroColuna, erro) {
    console.error('Ocorreu um erro global:', mensagem, origem, numeroLinha, numeroColuna, erro);
};
```

Neste exemplo, `window.onerror` é configurado para ser chamado sempre que ocorrer um erro global no navegador. Os parâmetros fornecidos (mensagem, origem, numeroLinha, numeroColuna, erro) contêm informações sobre o erro.

## No Node.js:

```javascript
// Configurando o evento process.on('uncaughtException') para capturar erros globais no Node.js
process.on('uncaughtException', function(erro) {
    console.error('Ocorreu um erro global:', erro);
});
```

No Node.js, `process.on('uncaughtException')` é utilizado para capturar erros globais. Da mesma forma que no exemplo do navegador, o callback fornece informações sobre o erro.

## Observações Importantes:

- **Navegador:** O evento `window.onerror` é acionado para erros de carregamento de recursos, erros de execução de JavaScript e outras exceções não tratadas no contexto global do navegador.

- **Node.js:** O evento `process.on('uncaughtException')` permite capturar erros não tratados em todo o processo Node.js. No entanto, é importante notar que usar esse evento pode deixar o estado do aplicativo em um estado imprevisível, e a aplicação pode continuar em execução mesmo após a ocorrência de erros graves.

**Observação:** Embora a captura global de erros seja útil para registrar informações, é preferível implementar tratamento de erros específico sempre que possível para ter mais controle sobre o comportamento do programa em situações de erro. A captura global de erros é uma ferramenta de último recurso.