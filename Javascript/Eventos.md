# Eventos em JavaScript

Eventos em JavaScript são ações ou ocorrências que acontecem em resposta a interações do usuário ou outras atividades no navegador. 
## **Adicionando Ouvintes de Eventos:**

### **Elemento HTML:**
```javascript
const meuElemento = document.getElementById('meuElemento');

meuElemento.addEventListener('click', function() {
    // Lógica a ser executada quando o elemento é clicado
});
```

### **Múltiplos Ouvintes:**
```javascript
meuElemento.addEventListener('click', funcaoUm);
meuElemento.addEventListener('mouseover', funcaoDois);
```

## **Tipos Comuns de Eventos:**

### **Click:**
```javascript
meuElemento.addEventListener('click', function() {
    // Lógica para lidar com um clique no elemento
});
```

### **Mouse Over:**
```javascript
meuElemento.addEventListener('mouseover', function() {
    // Lógica para lidar com o mouse sobre o elemento
});
```

### **Submit (Formulários):**
```javascript
const meuFormulario = document.getElementById('meuFormulario');

meuFormulario.addEventListener('submit', function(event) {
    event.preventDefault(); // Impede a submissão padrão do formulário
    // Lógica para lidar com a submissão do formulário
});
```

### **Key Press:**
```javascript
document.addEventListener('keypress', function(event) {
    // Lógica para lidar com uma tecla pressionada
});
```

## **Removendo Ouvintes de Eventos:**

```javascript
meuElemento.removeEventListener('click', funcaoUm);
```

## **Eventos de Janela:**

### **Carregamento da Página:**
```javascript
window.addEventListener('load', function() {
    // Lógica a ser executada quando a página está completamente carregada
});
```

### **Redimensionamento da Janela:**
```javascript
window.addEventListener('resize', function() {
    // Lógica para lidar com o redimensionamento da janela
});
```

## **Eventos de Tempo:**

### **Timeout:**
```javascript
setTimeout(function() {
    // Lógica a ser executada após um intervalo de tempo
}, 1000); // 1000 milissegundos (1 segundo)
```

### **Intervalo:**
```javascript
setInterval(function() {
    // Lógica a ser repetida em intervalos regulares
}, 2000); // 2000 milissegundos (2 segundos)
```
