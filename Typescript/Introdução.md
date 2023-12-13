# **TypeScript**

O TypeScript é um superset do JavaScript que adiciona tipagem estática e outros recursos ao JavaScript. Abaixo, você encontrará um cheatsheet com os conceitos e padrões mais comuns do TypeScript.

## Instalação

```bash
yarn add typescript
```

```bash
npm install typescript --save-dev
```

## Declaração de Variáveis

```typescript
let nome: string = "Alice";
let idade: number = 30;
let ativo: boolean = true;
let listaDeNomes: string[] = ["Alice", "Bob", "Carol"];
let tupla: [string, number] = ["Alice", 30]; // Tupla
```

## Funções

```typescript
function saudacao(nome: string): string {
  return `Olá, ${nome}!`;
}

const resultado: string = saudacao("Alice");
```

## Tipos Personalizados (Interfaces e Tipos)

```typescript
interface Pessoa {
  nome: string;
  idade: number;
}

type Cores = "vermelho" | "azul" | "verde";

const pessoa: Pessoa = { nome: "Alice", idade: 30 };
const cor: Cores = "vermelho";
```

## Classes

```typescript
class Carro {
  marca: string;

  constructor(marca: string) {
    this.marca = marca;
  }

  dirigir() {
    console.log(`Dirigindo um carro ${this.marca}`);
  }
}

const meuCarro = new Carro("Toyota");
meuCarro.dirigir();
```

## Herança

```typescript
class Animal {
  nome: string;

  constructor(nome: string) {
    this.nome = nome;
  }

  fazerBarulho() {
    console.log("Barulho genérico");
  }
}

class Cachorro extends Animal {
  fazerBarulho() {
    console.log("Au au!");
  }
}

const cachorro = new Cachorro("Buddy");
cachorro.fazerBarulho();
```

## Generics

```typescript
function primeiroElemento<T>(array: T[]): T {
  return array[0];
}

const primeiroNome: string = primeiroElemento(["Alice", "Bob", "Carol"]);
```

## Módulos

**`math.ts`**
```typescript
export function somar(a: number, b: number): number {
  return a + b;
}
```

**`app.ts`**
```typescript
import { somar } from "./math";

const resultado: number = somar(5, 3);
```
