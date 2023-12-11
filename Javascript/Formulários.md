# Manipulação de Formulários em JavaScript

Formulários em JavaScript são elementos cruciais para interatividade em páginas web.

## **Seleção de Elementos:**

### **Pelo ID:**
```javascript
const meuFormulario = document.getElementById('meuFormulario');
```

### **Pelo Nome do Formulário:**
```javascript
const formularioPorNome = document.forms['nomeDoFormulario'];
```

### **Pelo Nome do Elemento:**
```javascript
const campoNome = document.forms['nomeDoFormulario']['nomeDoCampo'];
```

## **Obtendo e Definindo Valores:**

### **Obter Valor do Campo:**
```javascript
const valorCampo = campoNome.value;
```

### **Definir Valor do Campo:**
```javascript
campoNome.value = 'Novo Valor';
```

## **Eventos de Formulário:**

### **Submissão do Formulário:**
```javascript
meuFormulario.addEventListener('submit', function(event) {
    event.preventDefault(); // Impede a submissão padrão do formulário
    // Lógica de manipulação dos dados do formulário
});
```

### **Mudança no Campo:**
```javascript
campoNome.addEventListener('change', function(event) {
    // Lógica a ser executada quando o valor do campo muda
});
```

## **Validando Formulários:**

### **Verificando se Campos estão Preenchidos:**
```javascript
if (campoNome.value === '' || campoEmail.value === '') {
    alert('Por favor, preencha todos os campos.');
}
```

### **Validando E-mail:**
```javascript
function validarEmail(email) {
    const re = /\S+@\S+\.\S+/;
    return re.test(email);
}

const emailValido = validarEmail(campoEmail.value);
```

## **Redirecionamento e Submissão Programática:**

### **Redirecionamento Após Submissão:**
```javascript
window.location.href = 'https://exemplo.com/sucesso';
```

### **Submissão Programática:**
```javascript
meuFormulario.submit();
```
