# SEO em HTML

O SEO (Search Engine Optimization) é essencial para melhorar a visibilidade e a classificação de uma página da web nos resultados de mecanismos de busca. Este cheatsheet fornece diretrizes sobre como otimizar seu código HTML para SEO.

## Tags de Cabeçalho

### **`<title>` (Título da Página):**

   - Cada página deve ter um título exclusivo e descritivo.
   - Inclua palavras-chave relevantes no título.

   ```html
   <title>Exemplo de Título de Página</title>
   ```

## **`<meta name="description">` (Descrição):**

   - Forneça uma descrição concisa e informativa da página.
   - Inclua palavras-chave relevantes.

   ```html
   <meta name="description" content="Uma breve descrição da página.">
   ```

## Estrutura de Conteúdo

### **`<h1>` a `<h6>` (Títulos):**

   - Use os elementos de título para estruturar seu conteúdo.
   - Inclua palavras-chave nos títulos, especialmente no `<h1>`.

   ```html
   <h1>Título Principal</h1>
   <h2>Subtítulo</h2>
   ```

### **`<p>` (Parágrafos):**

   - Estruture o conteúdo em parágrafos legíveis.
   - Inclua palavras-chave naturalmente.

   ```html
   <p>Este é um parágrafo de exemplo com palavras-chave relevantes.</p>
   ```

## Tags de Imagem

### **`<img>` (Imagens):**

   - Use o atributo `alt` para descrever imagens de forma significativa.
   - Inclua palavras-chave relevantes no atributo `alt`.

   ```html
   <img src="imagem.jpg" alt="Descrição significativa com palavras-chave relevantes">
   ```

## Links

### **`<a>` (Links):**

   - Use links âncora com texto âncora descritivo e relevante.
   - Evite "clique aqui" como texto de âncora.

   ```html
   <a href="pagina.html">Texto de âncora relevante</a>
   ```

## Estrutura de URL

### **URLs Amigáveis:**

   - Utilize URLs descritivas e amigáveis, incluindo palavras-chave.
   - Evite URLs complexas com parâmetros.

   ```html
   <a href="/produto/nome-do-produto">Exemplo.com/produto/nome-do-produto</a>
   ```

## Tags de Cabeçalho HTML

### **`<meta name="viewport">` (Viewport):**

   - Configure a viewport para dispositivos móveis.
   - Garanta que seu site seja responsivo.

   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   ```

## Sitemaps e Robots.txt

### **Sitemap XML:**

   - Crie um sitemap XML que liste todas as páginas do seu site.
   - Envie-o para mecanismos de busca por meio do Google Search Console.

   ```html
   <link rel="sitemap" type="application/xml" title="Sitemap" href="/sitemap.xml">
   ```

### **Robots.txt:**

    - Crie um arquivo `robots.txt` para controlar o acesso de mecanismos de busca a partes do seu site.

    ```
    User-agent: *
    Disallow: /pasta-restrita/
    ```

Utilize essas diretrizes de SEO em HTML para otimizar seu site para mecanismos de busca, melhorar a classificação e aumentar a visibilidade nos resultados de pesquisa. Lembre-se de que o conteúdo de alta qualidade e a experiência do usuário são fundamentais para um SEO eficaz.