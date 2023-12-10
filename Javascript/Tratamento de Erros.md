# Tratamento de Erros

A detecção de erros em JavaScript é fundamental para escrever um código robusto e confiável. O JavaScript fornece diversos mecanismos para detectar e lidar com erros durante a execução do seu programa.

## Declaração Try...Catch

A declaração `try...catch` é usada para lidar com exceções (erros) que podem ocorrer dentro de um bloco de código.

```javascript
try {
    // Código que pode lançar um erro
} catch (erro) {
    // Código para lidar com o erro
}
```

### Exemplo:

```javascript
try {
    const resultado = 10 / 0;
    console.log(resultado); // Isso não será executado devido ao erro
} catch (erro) {
    console.error('Ocorreu um erro:', erro.message);
}
```

## Objetos de Erro

O JavaScript fornece diferentes tipos de objetos de erro que podem ser capturados usando `try...catch`. Tipos comuns de erro incluem `Error`, `SyntaxError`, `TypeError`, `ReferenceError` e outros. Esses objetos de erro têm propriedades como `name` e `message`.

```javascript
try {
    // Código que pode lançar um erro
} catch (erro) {
    if (erro instanceof TypeError) {
        console.error('Ocorreu um erro de tipo:', erro.message);
    } else if (erro instanceof SyntaxError) {
        console.error('Ocorreu um erro de sintaxe:', erro.message);
    } else {
        console.error('Ocorreu um erro:', erro.message);
    }
}
```

## Bloco `finally`

O bloco `finally` é executado independentemente de um erro ter ocorrido ou não. Ele é frequentemente usado para realizar operações de limpeza.

```javascript
try {
    // Código que pode lançar um erro
} catch (erro) {
    // Código para lidar com o erro
} finally {
    // Código que sempre é executado
}
```

## Declaração `throw`

Você pode lançar manualmente um erro usando a declaração `throw`. Você pode lançar qualquer valor, mas é comum usar uma instância de `Error` ou suas subclasses.

```javascript
function dividir(a, b) {
    if (b === 0) {
        throw new Error('Divisão por zero');
    }
    return a / b;
}

try {
    const resultado = dividir(10, 0);
    console.log(resultado);
} catch (erro) {
    console.error('Ocorreu um erro:', erro.message);
}
```

Uma detecção e tratamento adequados de erros contribuem para uma melhor qualidade do código e experiência do usuário, pois evitam travamentos inesperados e facilitam o diagnóstico e a correção de problemas no código.