# **Generics em TypeScript**

Generics em TypeScript permitem que você crie componentes e funções reutilizáveis que trabalham com vários tipos de dados.

## **Declaração de Função Genérica:**

   ```typescript
   function echo<T>(arg: T): T {
     return arg;
   }
   ```

   - Use `<T>` para declarar um tipo genérico.
   - `arg: T` significa que o argumento também deve ter o mesmo tipo.

### **Uso de Função Genérica:**

   ```typescript
   const result = echo("Hello, Generics!");
   const numberResult = echo(42);
   ```
   - Chame a função genérica com diferentes tipos de argumentos.

## **Classe Genérica:**

   ```typescript
   class Wrapper<T> {
     private value: T;

     constructor(value: T) {
       this.value = value;
     }

     getValue(): T {
       return this.value;
     }
   }
   ```

   - Crie classes genéricas para encapsular valores de diferentes tipos.

### **Uso de Classe Genérica:**

   ```typescript
   const stringWrapper = new Wrapper("Hello, Generics!");
   const numberWrapper = new Wrapper(42);
   ```

   - Crie instâncias de classes genéricas com diferentes tipos.

## **Generics em Interfaces:**

   ```typescript
   interface Pair<T, U> {
     first: T;
     second: U;
   }
   ```

   - Use generics em interfaces para descrever objetos com tipos dinâmicos.


## **Restrições Genéricas:**

   ```typescript
   function length<T extends { length: number }>(arg: T): number {
     return arg.length;
   }
   ```

   - `T extends { length: number }` restringe o tipo genérico `T` a tipos que têm uma propriedade `length`.


Generics são uma ferramenta poderosa para escrever código reutilizável e flexível em TypeScript. Eles permitem que você escreva funções e classes que funcionam com uma variedade de tipos, mantendo a segurança de tipo ao mesmo tempo.