# Arrays

Arrays são estruturas de dados em JavaScript que permitem armazenar uma coleção de elementos. Eles podem ser usados para armazenar listas de valores e são muito versáteis.

## Criando um Array

```javascript
const meuArray = [1, 2, 3, 4, 5];
```

## Acessando Elementos

```javascript
const primeiroElemento = meuArray[0]; // Primeiro elemento (índice 0)
const ultimoElemento = meuArray[meuArray.length - 1]; // Último elemento
```

## Modificando Elementos

```javascript
meuArray[2] = 10; // Modifica o terceiro elemento para 10
```

## Adicionando e Removendo Elementos

### Adicionar ao Final

```javascript
meuArray.push(6); // Adiciona 6 ao final do array
```

### Remover do Final

```javascript
const ultimoRemovido = meuArray.pop(); // Remove e retorna o último elemento
```

### Adicionar no Início

```javascript
meuArray.unshift(0); // Adiciona 0 no início do array
```

### Remover do Início

```javascript
const primeiroRemovido = meuArray.shift(); // Remove e retorna o primeiro elemento
```

## Iterando em um Array

```javascript
for (let i = 0; i < meuArray.length; i++) {
    console.log(meuArray[i]);
}

meuArray.forEach(elemento => {
    console.log(elemento);
});
```

```java
const meuArray = ['a', 'b', 'c', 'd'];

meuArray.forEach((n, i) => {
  console.log(`Elemento: ${n}, Índice: ${i}`);
});
```

## Map, Filter e Reduce

```javascript
const novoArray = meuArray.map(item => item * 2); // Cria um novo array com elementos dobrados

const filtrado = meuArray.filter(item => item > 3); // Cria um novo array com elementos maiores que 3

const soma = meuArray.reduce((acumulador, atual) => acumulador + atual, 0); // Calcula a soma dos elementos
```
## Ordenação

```javascript
const arrayDesordenado = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5];
const arrayOrdenado = arrayDesordenado.sort(); // Ordena os elementos em ordem alfabética
```

## Concatenação

```javascript
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];
const arrayConcatenado = array1.concat(array2); // [1, 2, 3, 4, 5, 6]
```

## Destruturação de Arrays

```javascript
const [primeiro, segundo, ...resto] = meuArray; // Destruturação com spread/rest
```

## Verificando a Existência de Elementos

```javascript
const contemNumero3 = meuArray.includes(3); // Verifica se o número 3 está no array
const indiceNumero3 = meuArray.indexOf(3); // Retorna o índice do número 3 (ou -1 se não encontrado)
```

## Join

O método `join()` é usado para transformar os elementos de uma lista (ou array) em uma única string. Esse método é útil quando você deseja criar uma representação de string legível da lista, com elementos separados por um delimitador específico. Aqui está como usar o método `join()`:

```javascript
const lista = ["maçã", "banana", "laranja", "uva"];

// Transforma a lista em uma string, separando os elementos por vírgulas
const listaComoString = lista.join(", ");

console.log(listaComoString);
// Saída: "maçã, banana, laranja, uva"
```

**Sintaxe:**

```javascript
array.join(delimitador);
```

- `array`: O array que você deseja transformar em uma string.
- `delimitador`: O caractere ou sequência de caracteres que será usado como separador entre os elementos na string resultante. Este é um argumento opcional; se não for especificado, os elementos serão separados por vírgulas por padrão.
