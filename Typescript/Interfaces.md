# **Interfaces em TypeScript**

As interfaces são uma parte fundamental do TypeScript e são usadas para definir a estrutura dos objetos ou classes.

## **Declaração de Interface:**

   ```typescript
   interface Person {
     name: string;
     age: number;
   }
   ```

   - Define uma interface chamada `Person` com propriedades `name` e `age`.

## **Implementação de Interfaces:**

   ```typescript
   const user: Person = { name: "Alice", age: 30 };
   ```

   - Objetos podem implementar interfaces, seguindo sua estrutura.

## **Propriedades Opcionais:**

   ```typescript
   interface Config {
     apiKey: string;
     logLevel?: number;
   }
   ```

   - Use `?` para tornar propriedades opcionais.

## **Propriedades Somente Leitura:**

   ```typescript
   interface Point {
     readonly x: number;
     readonly y: number;
   }
   ```

   - Use `readonly` para criar propriedades que não podem ser modificadas após a inicialização.

## **Extendendo Interfaces:**

   ```typescript
   interface Employee extends Person {
     employeeId: number;
   }
   ```

   - Uma interface pode herdar de outra usando a palavra-chave `extends`.


## **Funções em Interfaces:**

   ```typescript
   interface Calculator {
     add(a: number, b: number): number;
   }
   ```

   - Interfaces podem definir a estrutura de funções.

## **Índices de Assinatura (Index Signatures):**

   ```typescript
   interface Dictionary {
     [key: string]: string;
   }
   ```

   - Crie interfaces que representam objetos com chaves dinâmicas.

## **Implementação de Interface:**

   ```typescript
   class Student implements Person {
     constructor(public name: string, public age: number) {}
   }
   ```

   - Classes podem implementar interfaces para garantir que cumpram um contrato.
