# Meta Tags em HTML

As meta tags são elementos HTML essenciais usados para fornecer informações sobre uma página da web. Elas desempenham um papel fundamental em SEO (Otimização para Mecanismos de Busca) e na exibição adequada de páginas em navegadores. Este cheatsheet apresenta as meta tags mais comuns e suas finalidades.

## Meta Tags Básicas

### `<meta charset="UTF-8">`

- Define o conjunto de caracteres da página como UTF-8.
- Permite que o navegador interprete e exiba corretamente caracteres especiais e acentuados.

### `<meta name="viewport" content="width=device-width, initial-scale=1.0">`

- Controla a escala e a largura da viewport para dispositivos móveis.
- Ajuda a tornar páginas responsivas em diferentes tamanhos de tela.

## Meta Tags de Descrição

### `<meta name="description" content="Descrição da Página">`

- Fornece uma descrição concisa da página para mecanismos de busca.
- A descrição é frequentemente exibida nos resultados de pesquisa como uma breve prévia do conteúdo.

### `<meta name="keywords" content="palavra-chave1, palavra-chave2, ...">`

- Lista palavras-chave relevantes para a página.
- Apesar de ser menos relevante para SEO atualmente, ainda pode ser útil para mecanismos de busca.

## Meta Tags de Autoria

### `<meta name="author" content="Nome do Autor">`

- Especifica o autor ou criador da página.
- Pode ser usado para créditos ou informações de contato.

## Meta Tags de Redirecionamento

### `<meta http-equiv="refresh" content="5;URL=https://novapagina.com">`

- Redireciona automaticamente o navegador para outra página após um determinado período (5 segundos no exemplo).
- Útil para redirecionamentos temporários.

## Meta Tags de Indexação

### `<meta name="robots" content="index, follow">`

- Controla o comportamento dos mecanismos de busca.
- "index" permite a indexação da página; "follow" permite que os mecanismos de busca sigam links na página.

### `<meta name="robots" content="noindex, nofollow">`

- Impede a indexação da página e a seguir links na página.
- Útil para páginas que você deseja excluir dos resultados de pesquisa.

## Meta Tags de Social Media

### `<meta property="og:title" content="Título da Página">`
### `<meta property="og:description" content="Descrição da Página">`
### `<meta property="og:image" content="URL-da-Imagem">`
### `<meta property="og:url" content="URL-da-Página">`

- Usadas para controlar como as páginas são exibidas quando compartilhadas em redes sociais (Open Graph Protocol).

## Meta Tags de Verificação

### `<meta name="google-site-verification" content="Código-de-Verificação">`

- Usada para verificar a propriedade de um site no Google Search Console.

Essas são algumas das meta tags mais comuns em HTML. Ao utilizá-las corretamente, você pode melhorar a indexação, a acessibilidade e a aparência das páginas da web em mecanismos de busca e em redes sociais. Certifique-se de adicionar as meta tags relevantes ao `<head>` do seu documento HTML para obter os melhores resultados.
