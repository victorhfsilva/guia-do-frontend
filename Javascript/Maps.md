# **`Map`**

O objeto `Map` é uma estrutura de dados que permite armazenar pares chave-valor, onde as chaves podem ser de qualquer tipo de dado, e os valores podem ser quaisquer valores, incluindo objetos. Aqui estão algumas operações comuns em um `Map`:

### **Criando um Map:**

   ```javascript
   const myMap = new Map();
   ```

### **Inserindo um par chave-valor:**

   ```javascript
   myMap.set('chave', 'valor');
   ```

### **Acessando um valor por chave:**

   ```javascript
   const valor = myMap.get('chave');
   ```

### **Verificando se uma chave existe:**

   ```javascript
   const existe = myMap.has('chave');
   ```

### **Removendo um par chave-valor por chave:**

   ```javascript
   myMap.delete('chave');
   ```

### **Iterando sobre os pares chave-valor:**

   ```javascript
   myMap.forEach((valor, chave) => {
     console.log(`Chave: ${chave}, Valor: ${valor}`);
   });
   ```

### **O método `keys()` retorna o iterador das chaves:**
    ```javascript
    for (let chaves of myMap.keys()){
        ...
    }
    ```

### **O método `values()` retorna o iterador dos valores:**
    ```javascript
    for (let valores of myMap.values()){
        ...
    }
    ```

## **`WeakMap`**

O `WeakMap` é uma estrutura de dados em JavaScript que oferece uma maneira de associar dados a objetos de forma que não impede a coleta de lixo desses objetos. Aqui estão os principais pontos a serem compreendidos sobre o `WeakMap`:

1. **Permite Apenas Objetos como Chaves:**
   - No `WeakMap`, apenas objetos podem ser usados como chaves. Tentar usar tipos primitivos (como números ou strings) resultará em um erro.

2. **Chaves "Fracas" e Coleta de Lixo:**
   - As chaves em um `WeakMap` são consideradas "fracas". Isso significa que, se não houver outras referências para uma chave fora do `WeakMap`, ela pode ser coletada pelo coletor de lixo.
   - Em outras palavras, se a única referência a um objeto é como chave em um `WeakMap` e não há outras referências a esse objeto em seu código, ele pode ser removido da memória durante a próxima coleta de lixo.

3. **Utilidade em Associações sem Impedir a Coleta de Lixo:**
   - O uso de `WeakMap` é particularmente útil quando você precisa associar dados específicos a objetos, mas não deseja impedir que esses objetos sejam coletados pelo coletor de lixo.
   - Isso é valioso em cenários onde a existência dos dados associados ao objeto é dependente da vida útil do objeto. Quando o objeto é coletado, os dados associados também podem ser removidos automaticamente.

#### Exemplo:

```javascript
// Criando um WeakMap
const mapaFraco = new WeakMap();

// Criando objetos para usar como chaves
const objetoChave1 = {};
const objetoChave2 = {};

// Associando dados aos objetos
mapaFraco.set(objetoChave1, 'Dados do Objeto 1');
mapaFraco.set(objetoChave2, 'Dados do Objeto 2');

// Obtendo dados associados aos objetos
console.log(mapaFraco.get(objetoChave1)); // 'Dados do Objeto 1'
console.log(mapaFraco.get(objetoChave2)); // 'Dados do Objeto 2'

// Quando os objetos de chaves são coletados, os dados associados também são removidos automaticamente
```

Neste exemplo, o `WeakMap` permite associar dados específicos a objetos (`objetoChave1` e `objetoChave2`) sem impedir que esses objetos sejam coletados pelo coletor de lixo. Se não houver mais referências para esses objetos, eles serão removidos da memória, e os dados associados também serão automaticamente eliminados pelo comportamento "fraco" do `WeakMap`.

### **Métodos Limitados:**

   `WeakMap` tem menos métodos em comparação com `Map`. Não é possível iterar sobre chaves ou valores diretamente. Isso ocorre porque as chaves são "fracas" e não é prático expô-las.

### **Não é Iterável:**

   `WeakMap` não é iterável, o que significa que você não pode usar um loop `for...of` para percorrer seus elementos.

### **Uso Comum:**

   `WeakMap` é frequentemente usado em estruturas de dados internas, como caches e armazenamento de dados privados em classes.

No geral, escolha entre `Map` e `WeakMap` com base nos requisitos de seu aplicativo. Use `Map` quando precisar de uma estrutura de dados de mapeamento flexível e segura para objetos-chave. Use `WeakMap` quando quiser associar dados a objetos sem impedir a coleta de lixo desses objetos.