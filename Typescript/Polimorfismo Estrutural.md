# **Polimorfismo Estrutural**

O polimorfismo estrutural é um conceito importante em programação orientada a objetos, onde objetos de diferentes classes podem ser tratados de forma polimórfica, desde que tenham uma estrutura compatível. No TypeScript, o polimorfismo estrutural é suportado e é uma parte fundamental da linguagem. Aqui está um resumo do polimorfismo estrutural:

### **Compatibilidade Estrutural:**

   - O polimorfismo estrutural se baseia na compatibilidade estrutural, onde os tipos são avaliados com base na estrutura de suas propriedades e métodos, em vez de sua origem ou classe.

### **Polimorfismo:**

   - O polimorfismo estrutural permite que objetos de diferentes classes interajam de maneira polimórfica, desde que compartilhem uma estrutura comum.
   - Isso facilita a reutilização de código, pois você pode criar funções e métodos que aceitam argumentos polimórficos.

### **Interfaces e Polimorfismo:**

   - Interfaces desempenham um papel importante no polimorfismo estrutural.
   - Uma classe que implementa uma interface é considerada compatível com essa interface, independentemente de sua origem.
   - Isso permite que objetos de diferentes classes sejam tratados de maneira uniforme quando implementam a mesma interface.

### **Tipos Compatíveis:**

   - Tipos são considerados compatíveis se suas estruturas forem compatíveis.
   - Isso significa que eles devem ter propriedades e métodos com nomes e tipos compatíveis.

## **Exemplo de Polimorfismo Estrutural:**

   ```typescript
   interface Animal {
     name: string;
     makeSound(): void;
   }

   class Dog implements Animal {
     constructor(public name: string) {}
     makeSound() {
       console.log(`${this.name} barks.`);
     }
   }

   class Cat implements Animal {
     constructor(public name: string) {}
     makeSound() {
       console.log(`${this.name} meows.`);
     }
   }

   function animalSound(animal: Animal) {
     animal.makeSound();
   }

   const dog = new Dog('Buddy');
   const cat = new Cat('Whiskers');

   animalSound(dog); // Polimorfismo: Dog faz som
   animalSound(cat); // Polimorfismo: Cat faz som
   ```

   - Neste exemplo, as classes `Dog` e `Cat` implementam a interface `Animal`.
   - A função `animalSound` aceita qualquer objeto que implemente `Animal`, permitindo o polimorfismo.

## **Polimorfismo Estrutural com Objetos Literais:**

   - O polimorfismo estrutural também se aplica a objetos literais que têm estruturas compatíveis.

   ```typescript
   interface Point {
     x: number;
     y: number;
   }

   function printCoordinates(point: Point) {
     console.log(`X: ${point.x}, Y: ${point.y}`);
   }

   const origin = { x: 0, y: 0 };
   const randomPoint = { x: 5, y: 10 };

   printCoordinates(origin); // Polimorfismo com objeto literal
   printCoordinates(randomPoint); // Polimorfismo com objeto literal
   ```

   - Objetos literais `origin` e `randomPoint` podem ser tratados de forma polimórfica porque têm a mesma estrutura.

O polimorfismo estrutural é uma característica poderosa do TypeScript que torna o código mais flexível e reutilizável, permitindo que diferentes tipos interajam de maneira consistente com base em sua estrutura compartilhada. Isso facilita a criação de código genérico e flexível em aplicações TypeScript.