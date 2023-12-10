# Estruturas de Repetição

As estruturas de repetição em JavaScript permitem executar um bloco de código repetidamente com base em uma condição ou um número específico de iterações.

## Loop `for`

```javascript
for (inicialização; condição; expressão final) {
    // Código a ser executado em cada iteração
}
```

### Exemplo:

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i); // 0, 1, 2, 3, 4
}
```

## Loop `while`

```javascript
while (condição) {
    // Código a ser executado enquanto a condição for verdadeira
}
```

### Exemplo:

```javascript
let contador = 0;
while (contador < 3) {
    console.log(contador); // 0, 1, 2
    contador++;
}
```

## Loop `do...while`

```javascript
do {
    // Código a ser executado pelo menos uma vez
} while (condição);
```

### Exemplo:

```javascript
let x = 0;
do {
    console.log(x); // 0
    x++;
} while (x < 0);
```

## Loop `for...in`

Usado para iterar sobre as propriedades enumeráveis de um objeto.

```javascript
for (let chave in objeto) {
    // Código a ser executado para cada propriedade
}
```

### Exemplo:

```javascript
const pessoa = {
    nome: "Alice",
    idade: 25,
    profissao: "Desenvolvedora"
};

for (let chave in pessoa) {
    console.log(chave, pessoa[chave]); // nome Alice, idade 25, profissao Desenvolvedora
}
```

## Loop `for...of`

Usado para iterar sobre elementos [iteráveis](./Iterator.md), como arrays, strings e outros objetos. 

```javascript
for (let elemento of iteravel) {
    // Código a ser executado para cada elemento
}
```

### Exemplo:

```javascript
const numeros = [1, 2, 3];

for (let numero of numeros) {
    console.log(numero); // 1, 2, 3
}
```

Lembre-se de que o uso apropriado de estruturas de repetição é fundamental para garantir que seu código seja eficiente e evite loops infinitos acidentais. Cada estrutura de repetição tem suas próprias situações de uso mais apropriadas.