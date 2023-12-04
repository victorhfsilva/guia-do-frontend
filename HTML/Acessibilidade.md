# Acessibilidade em HTML

A acessibilidade em HTML é fundamental para garantir que todos os usuários, incluindo aqueles com deficiências, possam acessar e interagir com o conteúdo da web. Este cheatsheet fornece diretrizes essenciais para criar páginas web mais acessíveis.

## Estrutura Básica

### **Declaração do tipo de documento:**

```html
<!DOCTYPE html>
```

### **Especifique a linguagem da página:**

```html
<html lang="pt-BR">
```

### **Use cabeçalhos HTML para criar uma estrutura de títulos significativa:**

```html
<h1>Título Principal</h1>
<h2>Subtítulo</h2>
```

## Texto Alternativo para Imagens

### **Adicione texto alternativo para todas as imagens:**

```html
<img src="imagem.jpg" alt="Descrição da Imagem">
```

## Semântica e Estrutura

### **Use tags semânticas para definir a estrutura da página:**

- `<header>`
- `<nav>`
- `<main>`
- `<section>`
- `<aside>`
- `<footer>`

## Links e Âncoras

### **Forneça rótulos descritivos para links:**

```html
<a href="pagina.html">Página de Exemplo</a>
```

### **Utilize âncoras para navegação interna:**

```html
<a href="#secao">Ir para a Seção</a>
```

## Tabelas

### **Cabeçalhos de tabela descritivos:**

```html
<th scope="col">Mês</th>
```

### **Agrupe células relacionadas com `<th>`:**

```html
<th id="jan">Janeiro</th>
```

## Formulários

### **Use rótulos associados a campos de entrada:**

```html
<label for="nome">Nome:</label>
<input type="text" id="nome" name="nome">
```

### **Forneça dicas de formato e requisitos em campos de entrada:**

```html
<input type="text" aria-describedby="dica-nome">
<div id="dica-nome">Digite seu nome completo.</div>
```

## Cores e Contraste

### **Garanta contraste adequado para o texto:**

- Verifique se o texto tem contraste suficiente em relação ao fundo.
- Utilize a ferramenta [Color Safe](http://colorsafe.co/) para verificar o nível de contraste entre duas cores.

### **Evite informações exclusivamente baseadas em cor:**

- Use símbolos ou texto adicional para complementar informações visuais.
- Utilize a ferramenta [Who Can Use](https://www.whocanuse.com/) para verificar quem consegue visualizar determinada cor.

## Recursos Multimídia

### **Forneça transcrições para conteúdo de áudio e vídeo:**

- Inclua transcrições para garantir que o conteúdo seja acessível.

## Testes e Validação

### **Valide seu código HTML:**

- Use ferramentas de validação como o [W3C Markup Validation Service](https://validator.w3.org/).

### **Teste com leitores de tela:**

   - Verifique como seu site é lido por leitores de tela, como o [NVDA](https://www.nvaccess.org/).

Lembre-se de que a acessibilidade na web é um processo contínuo. Ao seguir essas diretrizes, você pode criar páginas mais inclusivas que atendam a uma ampla variedade de usuários. Certifique-se de estar sempre atualizado com as diretrizes de acessibilidade web e boas práticas.