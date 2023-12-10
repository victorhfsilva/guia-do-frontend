# **`Set`**

O objeto `Set` é uma estrutura de dados que permite armazenar valores únicos de qualquer tipo. Aqui estão algumas operações comuns em um `Set`:

### **Criando um Set:**

   ```javascript
   const mySet = new Set();
   ```

### **Adicionando valores ao Set:**

   ```javascript
   mySet.add('valor');
   mySet.add(42);
   ```

### **Verificando se um valor existe:**

   ```javascript
   const existe = mySet.has('valor');
   ```

### **Removendo um valor do Set:**

   ```javascript
   mySet.delete('valor');
   ```

### **Tamanho do Set:**

   ```javascript
   const tamanho = mySet.size;
   ```

### **Iterando sobre os valores do Set:**

   ```javascript
   mySet.forEach((valor) => {
     console.log(`Valor: ${valor}`);
   });
   ```

## **`WeakSet`**

O `WeakSet` é uma estrutura de dados em JavaScript que permite armazenar objetos de forma que não impede a coleta de lixo desses objetos. Abaixo estão os principais conceitos relacionados ao `WeakSet`:

1. **Permite Apenas Objetos como Valores:**
   - No `WeakSet`, apenas objetos podem ser usados como valores. Tentar usar tipos primitivos resultará em um erro.

2. **Valores "Fracos" e Coleta de Lixo:**
   - Os valores em um `WeakSet` são considerados "fracos". Isso significa que, se não houver outras referências para um valor fora do `WeakSet`, ele pode ser coletado pelo coletor de lixo.
   - Se a única referência a um objeto é como valor em um `WeakSet` e não há outras referências a esse objeto em seu código, ele pode ser removido da memória durante a próxima coleta de lixo.

3. **Utilidade em Manter uma Lista de Objetos Fracos:**
   - O uso de `WeakSet` é útil quando você deseja manter uma lista de objetos, mas não quer impedir que esses objetos sejam coletados pelo coletor de lixo.
   - Isso é especialmente útil em cenários onde a existência dos objetos na lista é condicional à existência de outras referências a esses objetos no código.

### Exemplo:

```javascript
// Criando um WeakSet
const conjuntoFraco = new WeakSet();

// Criando objetos para usar como valores
const objetoValor1 = { id: 1 };
const objetoValor2 = { id: 2 };

// Adicionando objetos ao WeakSet
conjuntoFraco.add(objetoValor1);
conjuntoFraco.add(objetoValor2);

// Verificando se um objeto está no WeakSet
console.log(conjuntoFraco.has(objetoValor1)); // true
console.log(conjuntoFraco.has(objetoValor2)); // true

// Quando os objetos de valores são coletados, eles são removidos automaticamente do WeakSet
```

Neste exemplo, o `WeakSet` permite manter uma lista de objetos (`objetoValor1` e `objetoValor2`) sem impedir que esses objetos sejam coletados pelo coletor de lixo. Quando não houver mais referências a esses objetos fora do `WeakSet`, eles serão automaticamente removidos da memória durante a coleta de lixo.

### **Métodos Limitados:**

   `WeakSet` tem menos métodos em comparação com `Set`. Não é possível verificar se um valor existe ou obter seu tamanho. Isso ocorre porque os valores são "fracos" e não é prático acessá-los diretamente.

### **Não é Iterável:**

   `WeakSet` não é iterável, o que significa que você não pode usar um loop `for...of` para percorrer seus elementos.

### **Uso Comum:**

   `WeakSet` é frequentemente usado para manter listas de objetos "fracos" que podem ser coletados quando não são mais referenciados.

Em resumo, escolha entre `Set` e `WeakSet` com base nos requisitos de seu aplicativo. Use `Set` quando precisar armazenar valores únicos e quiser acessar e verificar esses valores posteriormente. Use `WeakSet` quando quiser manter referências a objetos "fracos" e permitir que eles sejam coletados quando não são mais referenciados.s