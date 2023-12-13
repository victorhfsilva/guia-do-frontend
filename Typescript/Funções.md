# **Funções em TypeScript**

## **Declaração de Função:**

   ```typescript
   function greet(name: string): string {
     return `Hello, ${name}!`;
   }
   ```

   - `function` define a função.
   - `name: string` é um parâmetro com um tipo.
   - `: string` após os parênteses indica o tipo de retorno da função.

## **Chamada de Função:**

   ```typescript
   const message = greet("Alice");
   ```

   - Chame a função fornecendo os argumentos necessários.

## **Parâmetros Opcionais:**

   ```typescript
   function greet(name: string, age?: number): string {
     if (age) {
       return `Hello, ${name}! You are ${age} years old.`;
     } else {
       return `Hello, ${name}!`;
     }
   }
   ```

   - O parâmetro `age` é opcional devido ao `?`.

## **Parâmetros Padrão:**

   ```typescript
   function greet(name: string, age: number = 30): string {
     return `Hello, ${name}! You are ${age} years old.`;
   }
   ```

   - O parâmetro `age` tem um valor padrão de `30`.

## **Funções de Setas (Arrow Functions):**

   ```typescript
   const add = (a: number, b: number): number => a + b;
   ```

   - Sintaxe curta e conveniente para funções.

## **Callbacks:**

   ```typescript
   function fetchData(url: string, callback: (data: any) => void) {
     // Lógica para buscar dados e chamar o callback.
   }
   ```

   - Use callbacks para realizar ações após a conclusão de uma tarefa assíncrona.

## **Funções Anônimas:**

   ```typescript
   const double = function (x: number): number {
     return x * 2;
   };
   ```

   - Funções sem nome atribuído a uma variável.

## **Funções Genéricas:**

   ```typescript
   function identity<T>(arg: T): T {
     return arg;
   }
   ```

   - Use `T` para criar funções genéricas que funcionam com diferentes tipos.

## **Overloads:**

   ```typescript
   function processInput(input: string): string;
   function processInput(input: number): number;
   function processInput(input: any): any {
     // Implementação com base no tipo de entrada.
   }
   ```

   - Defina várias assinaturas para a mesma função com base em tipos de entrada.

## **Funções como Tipos:**

   ```typescript
   type MathFunction = (x: number, y: number) => number;
   const add: MathFunction = (a, b) => a + b;
   ```

   - Use tipos para descrever funções e atribuí-las a variáveis.

## **Recursão:**

    ```typescript
    function factorial(n: number): number {
      if (n === 0) {
        return 1;
      }
      return n * factorial(n - 1);
    }
    ```

    - Funções podem chamar a si mesmas em cenários de recursão.

## **Funções Declaradas como Void**

   ```typescript
   function logMessage(message: string): void {
     console.log(message);
   }
   ```

   - `: void` indica que a função não retorna um valor.

   - Embora as funções `void` normalmente não retornem um valor, você ainda pode usar `return` sem um valor para encerrar a execução da função.

   ```typescript
   function doSomething(): void {
     console.log("Doing something.");
     return;
   }
   ```

   - `return;` é usado para sair da função.

## **Tipo `never`**

O tipo `never` em TypeScript representa um conjunto de valores que nunca ocorre. É comumente usado para indicar que uma função nunca retorna ou lança uma exceção que interrompe a execução do programa.

Aqui estão os principais usos e características do tipo `never`:

- **Funções que Nunca Retornam:**

   O tipo `never` é frequentemente usado para descrever funções que nunca retornam ao chamador. Isso pode ocorrer quando a função entra em um loop infinito, lança uma exceção que termina a execução do programa ou tem uma condição de retorno inalcançável.

   ```typescript
   function throwError(message: string): never {
     throw new Error(message);
   }
   ```

   - A função `throwError` lança uma exceção e não retorna, resultando em um tipo `never`.

- **Casos de Uso:**

   O tipo `never` é útil para:

   - Lidar com funções que lançam exceções e nunca retornam.
   - Indicar que um código nunca deve ser alcançado devido a verificações ou validações anteriores.
   - Representar funções que estão em um loop infinito (por exemplo, servidores em execução contínua).

- **Inferência de Tipos:**

   O tipo `never` geralmente não precisa ser anotado explicitamente, pois o TypeScript é capaz de inferir seu uso. No entanto, em casos onde a inferência não é possível, você pode anotar uma função ou variável com `: never`.

   ```typescript
   function unreachableCode(): never {
     while (true) {
       // Loop infinito
     }
   }
   ```
