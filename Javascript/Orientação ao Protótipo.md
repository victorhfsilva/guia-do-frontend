# **Orientação a Protótipos em JavaScript**

A orientação a protótipos é um conceito fundamental em JavaScript, que difere de outras linguagens de programação baseadas em classes. 

## Conceitos Básicos

### **Objetos em JavaScript:** 

Tudo em JavaScript é um objeto ou pode ser tratado como um objeto.

### **Protótipo:** 

Cada objeto em JavaScript tem uma propriedade interna chamada `prototype` que aponta para outro objeto. Essa propriedade é usada para herança de propriedades e métodos.

### **Construtores:** 

Funções em JavaScript podem ser usadas como construtores para criar objetos. Por convenção, nomes de construtores começam com letra maiúscula.

```javascript
function Carro(modelo) {
  this.modelo = modelo;
}

const meuCarro = new Carro("Sedan");
```

## Herança de Protótipos

Em JavaScript, a herança de protótipos permite que objetos herdem propriedades e métodos de seus protótipos. É possível adicionar métodos e propriedades ao protótipo de um construtor para que todos os objetos criados a partir desse construtor herdem essas características.

```javascript
// Adicionando um método ao protótipo do construtor Carro
Carro.prototype.acelerar = function() {
  console.log(`${this.modelo} acelerando...`);
};
```

### **Método `Object.create()`:**

Para criar objetos com protótipos específicos, você pode usar o método `Object.create()`.

```javascript
// Criando um novo objeto com o protótipo do construtor Carro
const novoCarro = Object.create(Carro.prototype);
```

### **Herança de Cadeia de Protótipos:**

Os objetos em JavaScript herdam propriedades e métodos de todos os protótipos em sua cadeia de protótipos.

### **`__proto__`:**

Cada objeto em JavaScript possui uma propriedade interna `__proto__` que aponta para seu protótipo. No entanto, é importante destacar que o uso direto de `__proto__` não é recomendado.

```javascript
// Verificando se o protótipo de meuCarro é igual ao protótipo do construtor Carro
console.log(meuCarro.__proto__ === Carro.prototype); // true
```

## Métodos Úteis

### **`Object.getPrototypeOf(obj)`:** 

Retorna o protótipo de um objeto.

```javascript
const prototipoDoCarro = Object.getPrototypeOf(meuCarro);
```

### **`Object.setPrototypeOf(obj, prototipo)`:** 

Define o protótipo de um objeto.

```javascript
Object.setPrototypeOf(meuCarro, Carro.prototype);
```

### **`Object.hasOwnProperty(prop)`:** 

Verifica se um objeto tem uma propriedade própria (não herdada).

```javascript
console.log(meuCarro.hasOwnProperty("modelo")); // true
```

## Palavras-chave `class` e `extends`

A partir do ECMAScript 6 (ES6), você pode usar a palavra-chave `class` para criar "classes" em JavaScript e `extends` para herdar de outra "classe".

```javascript
class Animal {
  constructor(nome) {
    this.nome = nome;
  }

  fazerSom() {
    console.log("Som genérico de animal.");
  }
}

class Cachorro extends Animal {
  fazerSom() {
    console.log("Latindo...");
  }
}

const meuCachorro = new Cachorro("Rex");
```