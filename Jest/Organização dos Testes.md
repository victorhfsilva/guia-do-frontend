# Organização de Testes:

O Jest fornece funções como `describe`, `beforeAll`, `afterAll`, `beforeEach` e `afterEach` para controlar o fluxo de execução dos seus testes e configurar contextos de teste específicos. Essas funções são úteis para organizar, configurar e limpar seu ambiente de teste.

## `describe`

A função `describe` é usada para agrupar testes relacionados em blocos. Isso ajuda a organizar seus testes em uma estrutura hierárquica.

```
describe ('Descrição do Teste', () => {
   //Testes
}
```

## `beforeAll`

A função `beforeAll` é usada para executar um bloco de código antes de todos os testes do grupo.

```javascript
describe('Grupo de Testes', () => {
    beforeAll(() => {
        // Configuração antes de todos os testes
    });

    // Seus testes aqui
});
```

## `afterAll`

A função `afterAll` é usada para executar um bloco de código após todos os testes do grupo.

```javascript
describe('Grupo de Testes', () => {
    afterAll(() => {
        // Limpeza após todos os testes
    });
    
    // Seus testes aqui
});
```

## `beforeEach`

A função `beforeEach` é usada para executar um bloco de código antes de cada teste no grupo. Isso é útil para preparar o ambiente antes de cada teste.

```javascript
describe('Grupo de Testes', () => {
    beforeEach(() => {
        // Configuração antes de cada teste
    });

    // Seus testes aqui
});
```

## `afterEach`

A função `afterEach` é usada para executar um bloco de código após cada teste no grupo. Isso é útil para realizar limpezas ou restaurações após cada teste.

```javascript
describe('Grupo de Testes', () => {
    afterEach(() => {
        // Limpeza após cada teste
    });

    // Seus testes aqui
});
```

## Diferenças entre `beforeAll`, `afterAll`, `beforeEach` e `afterEach`

- `beforeAll`: Executado uma vez antes de todos os testes no grupo.
- `afterAll`: Executado uma vez após todos os testes no grupo.
- `beforeEach`: Executado antes de cada teste no grupo.
- `afterEach`: Executado após cada teste no grupo.

Essas funções são úteis para manter seu ambiente de teste consistente, configurar pré-requisitos e evitar interferências entre diferentes testes. Eles ajudam a criar testes mais independentes e confiáveis.

## Test.each

O `test.each` é uma função fornecida pelo framework de testes Jest que permite executar um conjunto de testes para várias combinações de parâmetros. Isso é especialmente útil quando você precisa testar várias situações sem repetir o mesmo código de teste várias vezes.

### Sintaxe Básica

```javascript
test.each(arrayDeCasos)(descrição, callback);
```

- `arrayDeCasos`: Uma matriz que contém matrizes de valores para cada caso de teste.
- `descrição`: Uma string de modelo que define a descrição do teste com placeholders.
- `callback`: Uma função que será executada para cada conjunto de valores.

### Exemplo

```javascript
test.each([
    [valor1, valor2, valorEsperado],
    [valor3, valor4, valorEsperado]
])('Teste com %p e %p deve retornar %p', (valor1, valor2, valorEsperado) => {
    const resultado = suaFuncao(valor1, valor2);
    expect(resultado).toBe(valorEsperado);
});
```

### Placeholder `%p`

O placeholder `%p` é usado para substituir um valor da matriz de casos no texto de descrição. O valor correspondente na matriz de casos será inserido na posição do `%p` na descrição.

### Exemplo de Placeholder

```javascript
test.each([
    ['maçã', 'vermelha'],
    ['banana', 'amarela']
])('Uma %p é %p', (fruta, cor) => {
    // ...
});
```

### Dicas

- Use o `_` como um placeholder quando não precisar de um valor em um caso específico.
- Seja consistente com a ordem dos valores na matriz de casos e nos parâmetros da função de callback.
- Use `toEqual`, `toBe`, ou outros matchers para verificar os resultados dos testes.
