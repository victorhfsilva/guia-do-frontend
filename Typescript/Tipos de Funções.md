# Interfaces de Tipos de Funções

Interfaces em TypeScript podem ser usadas para descrever tipos de funções, como predicados. Aqui estão algumas interfaces que descrevem tipos de funções comuns:

1. **Predicado Simples:**

   ```typescript
   interface Predicate {
     (value: any): boolean;
   }
   ```

   - Esta interface descreve um predicado simples que recebe um valor e retorna um booleano.

2. **Predicado com Parâmetros Tipados:**

   ```typescript
   interface TypedPredicate<T> {
     (value: T): boolean;
   }
   ```

   - Esta interface permite que você defina um predicado com um tipo específico para o valor.

3. **Função de Mapeamento:**

   ```typescript
   interface Mapper<T, U> {
     (value: T): U;
   }
   ```

   - Esta interface descreve uma função de mapeamento que converte um valor de um tipo em outro.

4. **Função de Redução:**

   ```typescript
   interface Reducer<T, U> {
     (accumulator: U, currentValue: T): U;
   }
   ```

   - Esta interface é usada para funções de redução que combinam valores em um único resultado.


5. **Função de Classificação:**

   ```typescript
   interface SortFunction<T> {
     (a: T, b: T): number;
   }
   ```

   - Esta interface descreve uma função de classificação que compara dois valores e retorna um número.

6. **Validador de Objeto:**

   ```typescript
   interface ObjectValidator<T> {
     (obj: T): boolean;
   }
   ```
   - Use esta interface para criar funções que validam objetos de um tipo específico.

Essas interfaces são flexíveis e podem ser usadas para definir tipos de funções com vários propósitos, como filtragem, mapeamento, redução, classificação e validação. Elas são úteis ao trabalhar com arrays, objetos e coleções de dados em TypeScript.