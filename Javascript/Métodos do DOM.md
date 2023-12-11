# Métodos do DOM em JavaScript

O Document Object Model (DOM) é uma representação estruturada de documentos HTML ou XML, permitindo que scripts manipulem dinamicamente o conteúdo, a estrutura e o estilo de uma página web. Abaixo estão alguns métodos comuns do DOM em JavaScript:

## **Seleção de Elementos:**

### **`getElementById(id)`**
- Retorna um elemento pelo seu ID.

```javascript
const meuElemento = document.getElementById('meuId');
```

### **`getElementsByClassName(className)`**
- Retorna uma coleção de elementos pelo nome da classe.

```javascript
const elementos = document.getElementsByClassName('minhaClasse');
```

### **`getElementsByTagName(tagName)`**
- Retorna uma coleção de elementos pelo nome da tag.

```javascript
const paragrafos = document.getElementsByTagName('p');
```

### **`querySelector(selector)`**
- Retorna o primeiro elemento que corresponde ao seletor CSS especificado.

```javascript
const meuElemento = document.querySelector('.minhaClasse');
```

### **`querySelectorAll(selector)`**
- Retorna todos os elementos que correspondem ao seletor CSS especificado.

```javascript
const todosOsParagrafos = document.querySelectorAll('p.intro');
```

## **Manipulação de Conteúdo:**

### **`innerHTML`**
- Obtém ou define o conteúdo HTML de um elemento.

```javascript
const conteudo = meuElemento.innerHTML;
meuElemento.innerHTML = '<p>Novo conteúdo</p>';
```

### **`innerText`**
- Obtém ou define o texto visível de um elemento, excluindo as tags HTML.

```javascript
const texto = meuElemento.innerText;
meuElemento.innerText = 'Novo texto';
```

### **`appendChild(node)`**
- Adiciona um nó como filho de outro nó.

```javascript
const novoElemento = document.createElement('div');
meuElemento.appendChild(novoElemento);
```

### **`removeChild(node)`**
- Remove um nó filho de outro nó.

```javascript
meuElemento.removeChild(novoElemento);
```

## **Estilo e Classe:**

### **`style`**
- A propriedade `style` permite manipular estilos diretamente.

```javascript
meuElemento.style.color = 'red';
```

### **`classList`**
- A propriedade `classList` fornece métodos para adicionar, remover e alternar classes.

```javascript
meuElemento.classList.add('novaClasse');
meuElemento.classList.remove('antigaClasse');
meuElemento.classList.toggle('minhaClasse');
```

## **Eventos:**

### **`addEventListener(event, callback)`**
- Adiciona um ouvinte de eventos a um elemento.

```javascript
meuElemento.addEventListener('click', minhaFuncao);
```

### **`removeEventListener(event, callback)`**
- Remove um ouvinte de eventos de um elemento.

```javascript
meuElemento.removeEventListener('click', minhaFuncao);
```

Estes são apenas alguns dos muitos métodos do DOM que estão disponíveis em JavaScript. O DOM oferece uma ampla gama de funcionalidades para interação dinâmica com elementos HTML, e a escolha do método depende da tarefa específica que você deseja realizar.