# Variáveis

## Declaração de Variáveis

Em TypeScript, você pode declarar variáveis usando `var`, `let` e `const`. A recomendação geral é usar `const` sempre que possível para criar variáveis imutáveis.

```typescript
const myConst: number = 42;
let myVar: string = "Hello";
```

### Variáveis Imutáveis

Use `const` para criar variáveis imutáveis.

```typescript
const pi = 3.14159;
// pi = 3.14; // Erro: Não é possível reatribuir a uma constante
```

### Diferença entre `var` e `let`

1. **Escopo de Bloco:** A principal diferença entre `var` e `let` é o escopo. Variáveis declaradas com `var` têm escopo de função, o que significa que são visíveis em toda a função em que foram declaradas. Por outro lado, variáveis declaradas com `let` têm escopo de bloco, o que significa que são visíveis apenas no bloco (um conjunto de chaves `{ }`) em que foram declaradas.

   Exemplo:

   ```typescript
   function example() {
     if (true) {
       var x = 10; // Escopo de função
       let y = 20; // Escopo de bloco
     }
     console.log(x); // 10
     console.log(y); // Erro, y não está definido aqui
   }
   ```

2. **Hoisting:** Variáveis declaradas com `var` são "elevadas" para o topo do escopo da função, o que significa que você pode acessá-las antes de declará-las no código. Isso pode levar a comportamentos inesperados e é uma fonte comum de erros. Variáveis declaradas com `let` não têm esse comportamento de "hoisting".

   Exemplo:

   ```typescript
   console.log(a); // undefined
   var a = 5;
   ```

   No exemplo acima, `a` é elevada, então não ocorre um erro. No entanto, o valor é `undefined`. Se você tentasse o mesmo com `let`, receberia um erro.

Portanto, a recomendação geral é usar `let` em vez de `var` ao escrever código em TypeScript, porque `let` tem um escopo de bloco mais seguro e evita problemas comuns associados ao `var`. Se você precisa de uma variável com escopo de função, é preferível usar `const` para criar uma variável imutável.


## Tipos de Dados

Você pode declarar tipos para variáveis, o que ajuda a evitar erros durante o desenvolvimento e a melhorar a legibilidade do código.

```typescript
let numberVar: number = 42;
let stringVar: string = "Hello, TypeScript";
let booleanVar: boolean = true;
let arrayVar: number[] = [1, 2, 3];
let objectVar: { name: string; age: number } = { name: "Alice", age: 30 };
```

### União de Tipos

Você pode criar variáveis que podem conter mais de um tipo.

```typescript
let numberOrString: number | string = 42;
numberOrString = "Hello";
```

### Any Type

Se você não souber o tipo de uma variável, você pode usar o tipo `any`.

```typescript
let unknownVar: any = "I can be anything";
```

### Variáveis Não Inicializadas

As variáveis declaradas em TypeScript sem inicialização terão o tipo `undefined`.

```typescript
let uninitializedVar: number;
console.log(uninitializedVar); // Saída: undefined
```

### Variáveis de Template String

Você pode usar template strings com variáveis.

```typescript
let name = "Alice";
let greeting = `Hello, ${name}!`;
```

### **Variáveis que Nunca Recebem Valor:**

   Variáveis declaradas com o tipo `never` geralmente indicam que elas nunca podem receber um valor. Isso pode ser útil em cenários em que você quer garantir que uma variável permaneça não inicializada.

   ```typescript
   let uninitializedValue: never;
   ```

   - `uninitializedValue` é declarada como `never` e não pode receber um valor.

## Variáveis Globais

No TypeScript, variáveis globais são variáveis declaradas fora de qualquer função ou bloco de código e estão acessíveis em qualquer parte do programa. Elas possuem escopo global e são frequentemente usadas para armazenar informações que precisam ser compartilhadas em todo o código. No entanto, o uso excessivo de variáveis globais deve ser evitado, uma vez que pode levar a problemas de manutenção e legibilidade do código.

```typescript
// Declaração de uma variável global
var globalVariable: number = 42;

// Variáveis globais podem ser acessadas em qualquer lugar do código
function printGlobal() {
  console.log(globalVariable);
}

// Variáveis globais podem ser modificadas de qualquer lugar do código
function modifyGlobal() {
  globalVariable = 10;
}
```

**Boas Práticas para Variáveis Globais no TypeScript:**

1. **Minimize o Uso:** Evite criar um grande número de variáveis globais. Use-as apenas quando necessário.

2. **Evite Modificações Desnecessárias:** Evite modificar variáveis globais de várias partes do código, pois isso pode tornar o programa difícil de entender e depurar.

3. **Mantenha a Legibilidade:** Escolha nomes descritivos para variáveis globais, para que outros desenvolvedores possam entender facilmente o propósito delas.

4. **Considere Alternativas:** Em muitos casos, é preferível passar variáveis como argumentos para funções ou usar outras abordagens, como o uso de classes ou módulos, para encapsular e compartilhar dados.

5. **Use "const" para Variáveis Imutáveis:** Se uma variável global não deve ser modificada após a sua inicialização, declare-a como `const` para evitar modificações acidentais.