# **Escopo de Variáveis em JavaScript**

O escopo de variáveis em JavaScript refere-se à região do código em que uma variável pode ser acessada ou modificada. O escopo determina onde uma variável é válida e quais partes do código têm acesso a ela. Existem dois principais tipos de escopo de variáveis em JavaScript: escopo global e escopo local.

## Escopo Global

Variáveis declaradas fora de qualquer função têm escopo global. Isso significa que essas variáveis são acessíveis em todo o código, incluindo dentro de funções.

```javascript
let globalVariable = "Eu sou global";

function minhaFuncao() {
    console.log(globalVariable); // Acesso à variável global
}

minhaFuncao(); // Saída: "Eu sou global"
console.log(globalVariable); // Também pode ser acessada aqui
```

No entanto, o uso excessivo de variáveis globais não é recomendado, pois pode levar a conflitos e dificultar o rastreamento de erros.

## Escopo Local

Variáveis declaradas dentro de uma função têm escopo local. Elas só são acessíveis dentro dessa função e não podem ser vistas ou modificadas fora dela.

```javascript
function outraFuncao() {
    let localVariable = "Eu sou local";
    console.log(localVariable); // Acesso à variável local
}

outraFuncao(); // Saída: "Eu sou local"
console.log(localVariable); // Isso resultará em um erro, pois localVariable não está definida aqui
```

Além disso, em JavaScript, blocos como loops e condicionais não criam escopo separado para variáveis declaradas com `var`, mas o fazem para variáveis declaradas com `let` e `const`.

```javascript
if (true) {
    var varScoped = "Eu sou variável com escopo de função";
    let blockScoped = "Eu sou variável com escopo de bloco";
}

console.log(varScoped); // Acessível fora do bloco (escopo de função)
console.log(blockScoped); // Isso resultará em um erro, pois blockScoped não está definida aqui
```

## Escopo Aninhado

Quando você tem funções aninhadas, cada função cria um novo escopo local. As funções internas têm acesso às variáveis das funções externas, mas o inverso não é verdadeiro.

```javascript
function externa() {
    let variavelExterna = "Externa";

    function interna() {
        let variavelInterna = "Interna";
        console.log(variavelExterna); // Acesso à variável da função externa
    }

    interna();
    console.log(variavelInterna); // Isso resultará em um erro, pois variavelInterna não está definida aqui
}

externa();
```

Entender o escopo de variáveis é crucial para escrever código limpo, organizado e evitando conflitos indesejados entre variáveis. O uso de `let` e `const` para declarar variáveis é recomendado para evitar problemas relacionados ao escopo global.