# Funções

As funções em JavaScript permitem encapsular blocos de código para serem reutilizados e organizados. Elas podem receber parâmetros e retornar valores. Aqui está um resumo das principais características das funções em JavaScript.

## Declaração de Função

```javascript
function nomeDaFuncao(parametro1, parametro2) {
    // Código a ser executado
}

const resultado = nomeDaFuncao(valor1, valor2);
```

## Expressão de Função

```javascript
// Definindo uma função por meio de uma expressão
const nomeDaFuncao = function(parametro1, parametro2) {
    // Código a ser executado
};

// Chamando a função com valores específicos
const resultado = nomeDaFuncao(valor1, valor2);
```

* A expressão de função não sofre hoisting, o que significa que ela não é movida para o topo do escopo. Portanto, é necessário declarar a função antes de utilizá-la.

## Arrow Function (Função de Flecha)

```javascript
// Definindo uma função de flecha
const nomeDaFuncao = (parametro1, parametro2) => {
    // Código a ser executado
};

// Chamando a função de flecha com valores específicos
const resultado = nomeDaFuncao(valor1, valor2);
```

* Em contraste com a Declaração de Função, a Arrow Function não herda o contexto do objeto pai. Isso significa que ela não tem seu próprio `this` e usa o `this` do escopo em que foi criada.

## Escopo de Função

Dentro de uma função, as variáveis são declaradas com escopo local, o que significa que elas são acessíveis apenas dentro dessa função e não podem ser utilizadas fora dela.

Exemplo:

```javascript
function exemploFuncao() {
    // Variável com escopo local
    let variavelLocal = "Esta é uma variável local.";

    // Pode ser acessada apenas dentro da função
    console.log(variavelLocal);
}

// Tentar acessar a variável fora da função resultará em um erro
// console.log(variavelLocal); // Isso resultaria em um erro
```

Neste exemplo, a variável `variavelLocal` é acessível apenas dentro da função `exemploFuncao`. Tentar acessá-la fora dessa função resultaria em um erro, demonstrando o escopo local das variáveis de função.

## Funções Aninhadas

Funções aninhadas referem-se à prática de definir uma função dentro do corpo de outra função, criando assim escopos aninhados.

Exemplo:

```javascript
function funcaoExterna() {
    // Código da função externa

    function funcaoInterna() {
        // Código da função interna
    }

    // Chamando a função interna dentro da função externa
    funcaoInterna();
}

// Chamando a função externa
funcaoExterna();
```

Neste exemplo, `funcaoInterna` é uma função aninhada dentro de `funcaoExterna`. As funções aninhadas podem acessar variáveis da função externa, criando uma estrutura de escopo que organiza e encapsula o código de maneira eficiente.

## Funções de Callback

As funções de callback são utilizadas ao serem passadas como argumentos para outras funções e são executadas posteriormente, proporcionando maior flexibilidade e modularidade ao código.

### Exemplo 1:

```javascript
// Função que recebe uma função de callback como parâmetro e a executa
function executar(callback) {
    callback();
}

// Chamada da função com uma função de callback anônima
executar(function() {
    console.log("Função de callback executada!");
});
```

Neste exemplo, a função `executar` recebe uma função de callback como argumento e a executa.

### Exemplo 2:

```javascript
// Função que utiliza uma função de callback para realizar uma operação
function calculadora(x, operacao, y) {
    console.log(operacao(x, y));
}

// Definição de uma função de callback (soma)
const soma = (x, y) => x + y;

// Utilização da calculadora com a função de callback (soma)
calculadora(2, soma, 5); // Imprime: 7
```

Neste segundo exemplo, a função `calculadora` recebe três argumentos: dois operandos e uma função de callback que representa uma operação a ser realizada. No caso, é utilizada a função de callback `soma` para calcular a soma de 2 e 5.

## IIFE (Immediately Invoked Function Expression)

Uma IIFE é uma função que é executada imediatamente após ser definida.

```javascript
(function() {
    console.log("IIFE executada!");
})();
```

## Closure

Uma closure é uma função que mantém acesso às variáveis de seu escopo pai, mesmo após a conclusão da execução desse escopo.

### Exemplo 1:

```javascript
// Função que retorna uma closure
function contador() {
    let contagem = 0;
    return function() {
        contagem++;
        return contagem;
    };
}

// Criando uma instância da closure
const incrementar = contador();
console.log(incrementar()); // Resultado: 1
console.log(incrementar()); // Resultado: 2
```

Neste exemplo, a função `contador` retorna uma closure que mantém uma variável `contagem`. Cada vez que a closure é chamada, a `contagem` é incrementada, mantendo o estado entre as chamadas.

### Exemplo 2:

```javascript
// Função que retorna uma closure para realizar uma soma parcial
function soma(x) {
    return function(y) {
        return x + y;
    };
}

// Utilizando a closure para realizar soma completa
console.log(soma(10)(2)); // Resultado: 12

// Criando uma instância da closure para soma parcial
const somaparcial = soma(12);
console.log(somaparcial(10)); // Resultado: 22
```

Neste segundo exemplo, a função `soma` retorna uma closure que realiza a soma de dois valores. Ao chamar `soma(10)(2)`, obtemos o resultado 12. Além disso, a closure também pode ser utilizada para criar uma instância de soma parcial, como mostrado em `somaparcial(10)`, onde o resultado é 22. A closure mantém a variável `x` acessível mesmo após a execução da função `soma`.


## **Invocação de Funções em JavaScript**

JavaScript oferece várias maneiras de invocar funções, cada uma com seus usos específicos.

### Invocação Direta

```javascript
function minhaFuncao(arg1, arg2) {
    console.log(arg1, arg2);
}

minhaFuncao("Olá", "Mundo"); // Invocação direta da função
```

- Invocação direta é a forma mais simples de chamar uma função.
- Os argumentos são passados diretamente na chamada da função.

### Usando `call` e `apply`

```javascript
const pessoa = {
    nome: 'Victor',
    idade: 30
}

function saudacao(prefixo) {
    console.log(`${prefixo}, ${this.nome}!`);
}

saudacao.call(pessoa, 'Olá'); // Usando call
saudacao.apply(pessoa, ['Saduações']); // Usando apply
```

- `call` e `apply` permitem primeiramente definir o contexto (`this`) e então passar argumentos para uma função explicitamente.
- A diferença entre eles está na forma como os argumentos são passados: `call` aceita uma lista de argumentos separados por vírgula, enquanto `apply` aceita um array de argumentos.

### Usando o Operador `new`

```javascript
function Pessoa(nome, idade) {
    this.nome = nome;
    this.idade = idade;
}

const pessoa1 = new Pessoa("Alice", 30); // Criando uma instância com o operador new
const pessoa2 = new Pessoa("Bob", 25);

console.log(pessoa1.nome); // Alice
console.log(pessoa2.idade); // 25
```

- O operador `new` é usado para criar uma nova instância de um objeto, chamando o construtor da função.
- Dentro do construtor, `this` refere-se à nova instância que está sendo criada.

### Resumo

- A invocação direta é a forma mais simples de chamar uma função.
- `call` e `apply` permitem definir o contexto e passar argumentos explicitamente.
- O operador `new` cria uma nova instância de um objeto a partir de um construtor.
- Escolha a abordagem que melhor se adapte às necessidades específicas de seu código.