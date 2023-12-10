# Estruturas Condicionais

As estruturas condicionais permitem que você tome decisões com base em condições específicas. Em JavaScript, você pode usar as instruções `if`, `else if`, `else` e o operador ternário para implementar lógica condicional.

## Instrução `if`

A instrução `if` permite executar um bloco de código se uma condição for verdadeira.

```javascript
if (condicao) {
    // Código a ser executado se a condição for verdadeira
}
```

## Instrução `if` / `else`

A instrução `if` / `else` permite executar um bloco de código se uma condição for verdadeira e outro bloco se a condição for falsa.

```javascript
if (condicao) {
    // Código a ser executado se a condição for verdadeira
} else {
    // Código a ser executado se a condição for falsa
}
```

## Instrução `if` / `else if` / `else`

Você pode usar múltiplas instruções `else if` para verificar várias condições.

```javascript
if (condicao1) {
    // Código a ser executado se a condição1 for verdadeira
} else if (condicao2) {
    // Código a ser executado se a condição2 for verdadeira
} else {
    // Código a ser executado se nenhuma das condições anteriores for verdadeira
}
```

## Operador Ternário

O operador ternário é uma maneira concisa de fazer uma escolha entre dois valores com base em uma condição.

```javascript
let resultado = condicao ? valorSeVerdadeiro : valorSeFalso;
```

## Exemplo de If

```javascript
let hora = new Date().getHours();

if (hora < 12) {
    console.log("Bom dia!");
} else if (hora < 18) {
    console.log("Boa tarde!");
} else {
    console.log("Boa noite!");
}
```

## Switch

A instrução `switch` é usada para avaliar diferentes casos com base em um valor.

```javascript
switch (expressao) {
    case valor1:
        // Código se expressao for igual a valor1
        break;
    case valor2:
        // Código se expressao for igual a valor2
        break;
    default:
        // Código se nenhum caso corresponder a expressao
}
```

Lembre-se de que cada caso precisa ter um `break` no final para evitar a execução dos casos seguintes.
