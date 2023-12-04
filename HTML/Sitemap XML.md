# **Sitemap XML**

Um Sitemap XML é um arquivo que ajuda os motores de busca a entender a estrutura e a hierarquia do conteúdo de um site. 

## Estrutura Básica do Sitemap XML:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
        <loc>URL_DA_PÁGINA</loc>
        <lastmod>DATA_ÚLTIMA_MODIFICAÇÃO</lastmod>
        <changefreq>FREQUÊNCIA_DE_ALTERAÇÃO</changefreq>
        <priority>PRIORIDADE</priority>
    </url>
    <!-- Adicione mais elementos <url> conforme necessário -->
</urlset>
```

## Elementos Principais:

- **\<url>**: Representa uma página no site.
    - **\<loc>**: URL da página.
    - **\<lastmod>**: Data da última modificação (formato YYYY-MM-DD).
    - **\<changefreq>**: Frequência de alteração (always, hourly, daily, weekly, monthly, yearly, never).
    - **\<priority>**: Prioridade da página (0.0 a 1.0).

## Exemplo:

```xml
<url>
    <loc>https://www.exemplo.com/pagina1</loc>
    <lastmod>2023-01-01</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
</url>
```

## Dicas Adicionais:

1. **Adicionar Sitemap no robots.txt:**
   - Para indicar a localização do sitemap para os motores de busca, adicione a seguinte linha no arquivo robots.txt: `Sitemap: URL_DO_SITEMAP.XML`

2. **Ferramentas Úteis:**
   - **[Google Search Console:](https://search.google.com/search-console/welcome)** Permite enviar sitemaps e monitorar a indexação.



Lembre-se de que o Sitemap XML é uma ferramenta poderosa para melhorar a indexação do seu site pelos motores de busca, proporcionando uma estrutura clara do conteúdo.