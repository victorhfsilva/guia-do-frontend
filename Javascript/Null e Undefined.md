# **Diferença entre `null` e `undefined` em JavaScript**

Em JavaScript, `null` e `undefined` são dois valores especiais que são frequentemente usados para representar a ausência de valor ou a falta de atribuição. No entanto, eles têm significados sutis e diferenças de comportamento. 

## `null`

- `null` é um valor atribuído explicitamente a uma variável, indicando que a variável não contém um objeto ou valor válido.
- É um valor que representa a intenção de ausência de valor ou vazio.
- `null` é um valor primitivo.
- Quando uma variável é definida como `null`, ela é explicitamente definida como "vazia" ou "nula".

```javascript
let valor = null;
console.log(valor); // null
console.log(typeof valor); // "object"
```

## `undefined`

- `undefined` indica que uma variável foi declarada, mas nenhum valor foi atribuído a ela.
- Pode ocorrer quando você declara uma variável sem inicializá-la, ou quando tenta acessar uma propriedade que não existe em um objeto.
- `undefined` é um valor primitivo.
- `undefined` é usado para representar a falta de valor ou quando um valor não foi definido.

```javascript
let variavelNaoDefinida;
console.log(variavelNaoDefinida); // undefined
console.log(typeof variavelNaoDefinida); // "undefined"
```

## Diferenças Importantes

1. **Atribuição**: Você pode atribuir explicitamente `null` a uma variável, enquanto `undefined` ocorre por padrão quando uma variável não é inicializada.

2. **Verificação de Tipo**: O tipo de `null` é "object", enquanto o tipo de `undefined` é "undefined".

3. **Acesso a Propriedades**: Ao tentar acessar uma propriedade de um objeto que não existe, você obtém `undefined`. No entanto, se uma propriedade existe, mas seu valor é `null`, você obterá `null`.

```javascript
let objeto = { propriedade: null };
console.log(objeto.propriedade); // null
console.log(objeto.propriedadeInexistente); // undefined
```

## Quando Usar Cada Um?

- Use `null` quando quiser representar explicitamente a ausência de valor, como inicializar uma variável que deve conter um objeto, mas ainda não tem um valor válido.
- Use `undefined` quando uma variável foi declarada, mas não foi atribuída com um valor. Isso geralmente ocorre por padrão.

