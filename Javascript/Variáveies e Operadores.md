# Variáveis

## Declaração de Variáveis

```javascript
// Declaração usando var (escopo de função)
var x = 10;

// Declaração usando let (escopo de bloco)
let y = 5;

// Declaração usando const (valor constante, escopo de bloco)
const PI = 3.14;
```

### Escopo de Variáveis

- Variáveis declaradas com `var` têm escopo de função.
- Variáveis declaradas com `let` e `const` têm escopo de bloco.

### Tipos de Dados

```javascript
let nome = "ChatGPT";
let idade = 25;
let altura = 1.75;
let isAtivo = true;
let lista = [1, 2, 3];
let objeto = { chave: "valor" };
let nulo = null;
let indefinido = undefined;
```

## Operadores

### Operadores Aritméticos

```javascript
let soma = 10 + 5;
let subtracao = 20 - 8;
let multiplicacao = 3 * 4;
let divisao = 15 / 3;
let resto = 10 % 3;
```

### Operadores de Atribuição

```javascript
let x = 5;
x += 3; // x = x + 3;
x -= 2; // x = x - 2;
x *= 4; // x = x * 4;
x /= 2; // x = x / 2;
x %= 3; // x = x % 3;
```

### Operadores de Comparação

```javascript
let a = 10;
let b = 5;

a == b; // Igualdade (valor)
a != b; // Desigualdade (valor)
a === b; // Igualdade estrita (valor e tipo)
a !== b; // Desigualdade estrita (valor ou tipo)
a > b; // Maior que
a < b; // Menor que
a >= b; // Maior ou igual a
a <= b; // Menor ou igual a
```

### Operadores Lógicos

```javascript
let p = true;
let q = false;

p && q; // E lógico (AND)
p || q; // Ou lógico (OR)
!p; // Negação lógica (NOT)
```

### Operador Ternário

```javascript
let idade = 20;
let podeBeber = idade >= 18 ? "Maior de idade." : "Menor de Idade";
```

### Operadores de Incremento/Decremento

```javascript
let contador = 0;

contador++; // Incremento por 1 (contador = contador + 1)
contador--; // Decremento por 1 (contador = contador - 1)
```

## Conversão de Tipos

```javascript
let numeroString = "5";
let numero = parseInt(numeroString); // Converte para número inteiro
let decimal = parseFloat("3.14"); // Converte para número decimal
let stringNumero = String(10); // Converte para string
```