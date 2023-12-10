
# Importações e Exportações

## Utilizando o `module.exports` e `require`

Em ambientes Node.js e CommonJS, você pode usar `module.exports` para exportar valores de um módulo e `require` para importá-los em outro módulo.

### Valores

#### Exportando Valores

```javascript
// arquivo: modulo.js
const valor1 = 10;
const valor2 = "abc";

module.exports = {
    valor1,
    valor2
};
```

#### Importando Valores

```javascript
// arquivo: outro-arquivo.js
const modulo = require('./modulo.js');

console.log(modulo.valor1); // 10
console.log(modulo.valor2); // "abc"
```

### Funções

#### Exportação de Função Única

```javascript
// arquivo: modulo.js
module.exports = minhaFuncao; // Exporta uma única função
```

#### Importação de Função Única

```javascript
// arquivo: outro-arquivo.js
const minhaFuncao = require('./modulo.js');
```

#### Exportação de Funções Nomeadas

```javascript
// arquivo: modulo.js
module.exports.funcao1 = function() {
    // ...
};

module.exports.funcao2 = function() {
    // ...
};
```

#### Importação de Funções Nomeadas

```javascript
// arquivo: outro-arquivo.js
const modulo = require('./modulo.js');

modulo.funcao1();
modulo.funcao2();
```

### Classes

#### Exportação de Classes

```javascript
// arquivo: classe.js
class MinhaClasse {
    // ...
}

module.exports = MinhaClasse;
```

#### Importação de Classes
```javascript
// arquivo: outro-arquivo.js
const MinhaClasse = require('./classe.js');
const instancia = new MinhaClasse();
```

### Destructuring

Para armazenar os atributos ou métodos importados em variáveis locais podemos utilizar o Destructuring para simplificar a sintaxe.

```javascript
// arquivo: modulo.js
const valor1 = 10;
const valor2 = "abc";

module.exports = {
    valor1,
    valor2
};

module.exports.funcao1 = function() {
    // ...
};
```

```javascript
const {valor1, valor2, funcao1} = require('./modulo.js')
```

## Utilizando o `export` e `import`

O recurso de importações e exportações permite que você modularize e organize seu código em módulos reutilizáveis. Ele é essencial para construir aplicações complexas e bem estruturadas em JavaScript.

### Default 

#### Exportação Padrão

```javascript
// arquivo: modulo.js
export default minhaFuncao; // Exporta a função como padrão
```

#### Importação Padrão

```javascript
// arquivo: outro-arquivo.js
import minhaFuncao from './modulo.js'; // Importa a função padrão
```

### Nomeada

#### Exportação Nomeada

```javascript
// arquivo: modulo.js
export function funcao1() {
    // ...
}

export function funcao2() {
    // ...
}
```

#### Importação Nomeada

```javascript
// arquivo: outro-arquivo.js
import { funcao1, funcao2 } from './modulo.js'; // Importa funcao1 e funcao2
```

#### Importação Nomeada com Renomeação

```javascript
// arquivo: modulo.js
export function funcao1() {
    // ...
}

export function funcao2() {
    // ...
}
```

```javascript
// arquivo: outro-arquivo.js
import { funcao1 as fn1, funcao2 as fn2 } from './modulo.js'; // Importa com nomes diferentes
```

### Exportação de Tudo como Objeto

```javascript
// arquivo: modulo.js
function funcao1() {
    // ...
}

function funcao2() {
    // ...
}

export default {
    funcao1,
    funcao2
};
```

```javascript
// arquivo: outro-arquivo.js
import modulo from './modulo.js'; // Importa tudo como um objeto
```

O uso de importações e exportações é fundamental para dividir seu código em módulos independentes e promover uma arquitetura modular e organizada em suas aplicações JavaScript. Certifique-se de estar familiarizado com esses conceitos ao desenvolver projetos mais complexos.