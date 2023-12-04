# Tipos de Links

### Link type "alternate"

- Define uma versão alternativa de uma página.
- Geralmente usado para especificar páginas em diferentes idiomas.

```html
<link rel="alternate" hreflang="es" href="https://www.example.com/es/">
```

### Link type "author"

- Define um link para a página de perfil do autor.
- Pode ser usado em artigos ou postagens de blog.

```html
<link rel="author" href="https://www.example.com/author/john-doe">
```

### Link type "canonical"

- Especifica a URL canônica de uma página.
- Ajuda os mecanismos de busca a evitar conteúdo duplicado.

```html
<link rel="canonical" href="https://www.example.com/page">
```

### Link type "stylesheet"

- Define um link para uma folha de estilo (CSS).
- Indica como a página deve ser estilizada.

```html
<link rel="stylesheet" type="text/css" href="styles.css">
```

### Link type "icon"

- Define um ícone da página, geralmente exibido na guia do navegador.
- Usado para favicons.

```html
<link rel="icon" href="favicon.ico" type="image/x-icon">
```

### Link type "prefetch"

- Sugere ao navegador que pré-carregue recursos.
- Pode acelerar o carregamento de páginas subsequentes.

```html
<link rel="prefetch" href="próxima-página.html">
```

### Link type "next" e "prev"

- Indica páginas relacionadas em uma série, como páginas de uma lista.
- Ajuda na navegação e SEO.

```html
<link rel="next" href="página-seguinte.html">
<link rel="prev" href="página-anterior.html">
```

Esses são alguns dos tipos de links mais comuns em HTML. Eles desempenham papéis importantes na estruturação, navegação e otimização de páginas da web. Certifique-se de usá-los adequadamente para melhorar a experiência do usuário e o desempenho do seu site.