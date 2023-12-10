# Objetos

Em JavaScript, objetos são estruturas de dados que podem armazenar múltiplos valores associados a chaves. Eles são usados para representar entidades complexas e suas propriedades.

## Criando Objetos

### Notação de Objeto Literal

```javascript
const pessoa = {
    nome: "Alice",
    idade: 25,
    profissao: "Desenvolvedora"
};
```

### Construtor de Objeto

```javascript
function Pessoa(nome, idade, profissao) {
    this.nome = nome;
    this.idade = idade;
    this.profissao = profissao;
}

const pessoa = new Pessoa("Bob", 30, "Designer");
```

### Função Construtora Object

```javascript
const pessoa = new Object();
pessoa.nome = "Bob";
pessoa.idade = 30;
pessoa.profissao = "Designer";
```

## Acessando Propriedades

```javascript
console.log(pessoa.nome); // "Alice"
console.log(pessoa["idade"]); // 25
```

## Adicionando e Modificando Propriedades

```javascript
pessoa.genero = "Feminino";
pessoa.idade = 26;
```

## Removendo Propriedades

```javascript
delete pessoa.profissao;
```

## Iterando sobre Propriedades

```javascript
for (let chave in pessoa) {
    console.log(chave, pessoa[chave]);
}
```

## Métodos

Métodos são funções definidas como propriedades de um objeto.

```javascript
const carro = {
    marca: "Toyota",
    modelo: "Corolla",
    ligar: function() {
        console.log("O carro está ligado.");
    }
};

carro.ligar(); // "O carro está ligado."
```

## Objeto Aninhado

Objetos podem ser aninhados dentro de outros objetos.

```javascript
const endereco = {
    rua: "Rua Principal",
    cidade: "Cidade Central"
};

const pessoa = {
    nome: "Eva",
    idade: 28,
    endereco: endereco
};
```

