# **Classes em TypeScript**

Classes em TypeScript são uma maneira de criar objetos com propriedades e métodos que compartilham um comportamento comum.

## **Declaração de Classe:**

   ```typescript
   class Animal {
     constructor(name: string) {
       this.name = name;
     }
   }
   ```

   - Você declara uma classe com a palavra-chave `class`.
   - O construtor `constructor` é um método especial usado para inicializar objetos.

## **Criando Objetos:**

   ```typescript
   const cat = new Animal('Whiskers');
   ```

   - Use a palavra-chave `new` para criar uma instância da classe.
   - O construtor é chamado quando você cria um novo objeto.

## **Propriedades de Classe:**

   ```typescript
   class Animal {
     name: string;

     constructor(name: string) {
       this.name = name;
     }
   }
   ```

   - Defina propriedades diretamente na classe.
   - Acesse essas propriedades com `this`.

## **Herança:**

   ```typescript
   class Dog extends Animal {
     breed: string;

     constructor(name: string, breed: string) {
       super(name);
       this.breed = breed;
     }
   }
   ```

   - Crie classes filhas que herdam de classes pai.
   - Use `super` no construtor da classe filha para chamar o construtor da classe pai.
   
## **Métodos de Classe:**

   ```typescript
   class Animal {
     speak(): void {
       console.log(`${this.name} says hello.`);
     }
   }
   ```

   - Declare métodos dentro da classe.
   - Chame esses métodos em instâncias da classe.

## **Métodos Estáticos:**

   ```typescript
   class MathUtil {
     static square(x: number): number {
       return x * x;
     }
   }
   ```

   - Use métodos estáticos para funções que não dependem de instâncias da classe.
   - Acesse-os diretamente na classe, não em instâncias.

## **Acesso Modificadores:**

   - TypeScript fornece modificadores de acesso como `public`, `private` e `protected` para controlar a visibilidade de propriedades e métodos.
   - Estes modificadores só são aplicados no lado do Typescript.

   Exemplo:

   ```typescript
   class Person {
     private name: string;

     constructor(name: string) {
       this.name = name;
     }
   }
   ```

    Outra forma de declarar um atributo como sendo privado é através do `#`:

   ```typescript
   class Person {
     #name: string;

     constructor(name: string) {
       this.name = name;
     }

     get name() {
      return this.#name;
     }
   }
   ```

## **Getter e Setter:**

   ```typescript
   class Circle {
     private _radius: number;

     get radius(): number {
       return this._radius;
     }

     set radius(value: number) {
       if (value >= 0) {
         this._radius = value;
       }
     }
   }
   ```

   - Use `get` e `set` para controlar a leitura e gravação de propriedades.

## **Argumentos:**

```typescript
class Exemplo {
  propriedade?: string; // Argumento opcional com '?'
  outraPropriedade!: number; // Asserção de não nulo com '!'
  readonly propriedadeSomenteLeitura: string = 'Este valor não pode ser alterado'; // Propriedade readonly
  #campoPrivado: string = 'Este campo é privado'; // Campo privado com '#'

  constructor(valor?: string) {
    this.propriedade = valor; // Atribuição de valor para a propriedade opcional
    this.outraPropriedade = 42; // Atribuição de valor para a propriedade não nula
    // this.propriedadeSomenteLeitura = 'Novo valor'; // Erro, propriedade readonly não pode ser reatribuída
    // this.#campoPrivado = 'Novo valor'; // Erro, campo privado não pode ser acessado diretamente
  }

  setCampoPrivado(novoValor: string) {
    // Método para alterar o campo privado
    this.#campoPrivado = novoValor;
  }
}
```

Aqui estão os detalhes sobre esses argumentos:

- `?` (Opcional): O operador `?` após o nome do argumento indica que ele é opcional. Você pode ou não fornecer um valor quando criar uma instância da classe.

- `!` (Assertão de Não Nulo): O operador `!` é usado após o nome do argumento para indicar que você tem certeza de que a propriedade não será `null` ou `undefined`. Use isso quando tem certeza de que a propriedade estará definida antes de ser acessada.

- `readonly`: A palavra-chave `readonly` é usada para criar propriedades cujos valores não podem ser alterados após a inicialização. Eles devem ser definidos durante a criação da instância da classe.

- `#` (Campo Privado): O `#` é usado para criar campos privados. Campos privados não podem ser acessados ou modificados de fora da classe. Eles fornecem encapsulamento e ocultam os detalhes de implementação da classe.

## **Interfaces:**

   ```typescript
   interface Printable {
     print(): void;
   }

   class Book implements Printable {
     print(): void {
       console.log('Printing the book...');
     }
   }
   ```

   - Classes podem implementar interfaces, garantindo que possuam métodos específicos.

**12. Classes Abstratas:**

   ```typescript
   abstract class Shape {
     abstract area(): number;
   }
   ```

   - Classes abstratas não podem ser instanciadas diretamente, mas fornecem uma base para outras classes.
   - São usadas para definir um contrato ou interface que as classes filhas devem seguir.
   - Classes abstratas podem conter métodos abstratos, que são declarados apenas, mas não têm implementação na classe abstrata.
   - As classes filhas devem fornecer implementações para todos os métodos abstratos da classe abstrata.

Exemplo:

```typescript
abstract class Shape {
  abstract area(): number;
}

class Circle extends Shape {
  constructor(private radius: number) {
    super();
  }

  area(): number {
    return Math.PI * this.radius * this.radius;
  }
}

class Rectangle extends Shape {
  constructor(private width: number, private height: number) {
    super();
  }

  area(): number {
    return this.width * this.height;
  }
}

const circle = new Circle(5);
const rectangle = new Rectangle(4, 6);

console.log(circle.area()); // Calcula a área do círculo
console.log(rectangle.area()); // Calcula a área do retângulo
```

- A classe `Shape` é abstrata e define um contrato para as classes filhas implementarem o método `area()`.
- As classes `Circle` e `Rectangle` herdam da classe abstrata `Shape` e fornecem implementações para o método `area()`.
- As classes filhas são obrigadas a implementar todos os métodos abstratos definidos na classe abstrata.
- As classes abstratas são úteis quando você deseja garantir que todas as classes filhas tenham comportamentos específicos.

