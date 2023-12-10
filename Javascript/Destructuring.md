# Destructuring de Objetos

O destructuring de objetos é uma técnica em JavaScript que permite extrair valores de objetos de maneira mais concisa, criando variáveis com base nas propriedades do objeto.

## Sintaxe Básica

```javascript
const { propriedade1, propriedade2 } = objeto;
```

### Exemplo

```javascript
const pessoa = {
    nome: 'Alice',
    idade: 30,
    profissao: 'Desenvolvedora'
};

const { nome, idade } = pessoa;

console.log(nome); // 'Alice'
console.log(idade); // 30
```

## Definindo Variáveis com Nomes Diferentes

```javascript
const { nome: nomePessoa, idade: idadePessoa } = pessoa;

console.log(nomePessoa); // 'Alice'
console.log(idadePessoa); // 30
```

## Valor Padrão

```javascript
const { cidade = 'Desconhecida' } = pessoa;

console.log(cidade); // 'Desconhecida'
```

## Ignorar Propriedades

Em JavaScript, a sintaxe de destructuring com o operador Rest (...) permite que você ignore ou colete as propriedades restantes de um objeto. Isso é particularmente útil quando você deseja extrair apenas algumas propriedades específicas e lidar com o restante de uma forma mais compacta.

```javascript
const { nome, ...outrasPropriedades } = pessoa;

console.log(nome); // 'Alice'
console.log(outrasPropriedades); // { idade: 30, profissao: 'Desenvolvedora' }
```

## Destructuring de Objetos Passados como Argumentos

```javascript
function exibirDados({ nome, idade }) {
    console.log(`Nome: ${nome}, Idade: ${idade}`);
}

exibirDados(pessoa); // Nome: Alice, Idade: 30
```

O destructuring de objetos é uma maneira poderosa de extrair informações de objetos de maneira mais legível e concisa, melhorando a clareza do seu código.