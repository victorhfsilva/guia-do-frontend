# Classes em JavaScript

Classes são uma forma de criar objetos reutilizáveis com propriedades e métodos. Elas são uma parte fundamental da programação orientada a objetos em JavaScript.

## Declaração de Classe

```javascript
class NomeDaClasse {
    constructor(parametros) {
        // Inicialização de propriedades
    }

    metodo1() {
        // Código do método
    }

    metodo2() {
        // Código do método
    }
}
```

## Construtor

O construtor é um método especial chamado quando uma nova instância da classe é criada. Ele é usado para inicializar propriedades.

```javascript
class Pessoa {
    constructor(nome, idade) {
        this.nome = nome;
        this.idade = idade;
    }
}
```

## Métodos

Métodos são funções definidas dentro da classe e podem ser chamados nas instâncias criadas a partir da classe.

```javascript
class Retangulo {
    constructor(largura, altura) {
        this.largura = largura;
        this.altura = altura;
    }

    calcularArea() {
        return this.largura * this.altura;
    }
}
```

## Herança

Classes podem herdar propriedades e métodos de outras classes usando a palavra-chave `extends`.

```javascript
class Animal {
    constructor(nome) {
        this.nome = nome;
    }

    fazerSom() {
        console.log("Som desconhecido");
    }
}

class Cachorro extends Animal {
    fazerSom() {
        console.log("Latido");
    }
}
```

## Método `super`

A palavra-chave `super` é usada dentro de uma classe filha para chamar o construtor ou métodos da classe pai.

```javascript
class Gato extends Animal {
    constructor(nome) {
        super(nome); // Chama o construtor da classe Animal
    }

    fazerSom() {
        console.log("Miado");
    }
}
```

## Getters e Setters

Getters e setters são métodos especiais usados para acessar e modificar propriedades de uma classe.

```javascript
class ContaBancaria {
    constructor(saldo) {
        this._saldo = saldo;
    }

    get saldo() {
        return this._saldo;
    }

    set saldo(valor) {
        if (valor >= 0) {
            this._saldo = valor;
        }
    }
}
```

## Classe Estática

Métodos estáticos pertencem à própria classe e não às instâncias. Eles são acessados diretamente na classe.

```javascript
class Utilitarios {
    static duplicar(valor) {
        return valor * 2;
    }
}

Utilitarios.duplicar(5); // 10
```
## Atributos e Métodos Privados

Embora não haja suporte nativo para tornar atributos e métodos completamente privados, você pode usar convenções para indicar que eles devem ser tratados como privados. Isso não impede que sejam acessados, mas sinaliza aos desenvolvedores que eles não devem ser manipulados diretamente. Isso ajuda a evitar o acesso direto a partes internas da classe e promove uma boa prática de desenvolvimento.

```javascript
class MinhaClasse {
    constructor() {
        this.publico = 42; // Atributo público
        this.#privado = 100; // Atributo interno
    }

    metodoPublico() {
        // Método público
    }

    #metodoPrivado() {
        // Método interno
    }
}
```