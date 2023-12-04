# **robots.txt**

O arquivo robots.txt é uma parte crucial da otimização para motores de busca (SEO), permitindo que os webmasters controlem quais partes de seus sites são acessíveis aos motores de busca. Aqui está um guia rápido para criar e entender um arquivo robots.txt:

## Estrutura Básica do robots.txt:

```plaintext
User-agent: [AGENTE_DO_MOTOR_DE_BUSCA]
Disallow: [CAMINHO_DO_DIRETÓRIO_OU_ARQUIVO]
Allow: [CAMINHO_ESPECÍFICO_SE_PERMITIDO]
```

- **User-agent:** Especifica o agente do motor de busca ao qual as regras se aplicam.
- **Disallow:** Indica os diretórios ou arquivos que devem ser excluídos do acesso.
- **Allow:** Permite acesso a diretórios ou arquivos específicos (opcional).

### Exemplo Prático:

```plaintext
User-agent: *
Disallow: /admin/
Allow: /public/
```

- Este exemplo permite que todos os agentes de motores de busca acessem o diretório `/public/` e nega acesso ao diretório `/admin/`.

## Dicas Adicionais:

1. **Wildcard (\*):** Use o asterisco como curinga para representar todos os agentes de motores de busca. Ex: `User-agent: *`.

2. **Sitemaps:**
   - Indique a localização do seu sitemap no robots.txt: `Sitemap: URL_DO_SITEMAP.XML`

3. **Caminhos Relativos:**
   - Os caminhos são relativos ao diretório raiz do domínio. Ex: `/images/` representa `https://www.example.com/images/`.

4. **Comentários:**
   - Use `#` para adicionar comentários. Ex: `# Este é um comentário`.

## Ferramentas Úteis:

1.  **[Google Search Console:](https://search.google.com/search-console/welcome)**
    - Permite testar e visualizar o arquivo robots.txt.


## Teste e Validação:

1. **Teste no Navegador:**
   - Acesse `https://www.example.com/robots.txt` para visualizar o arquivo.

2. **Google Search Console:**
   - Use a ferramenta de teste de robots.txt no Google Search Console para verificar erros.

O robots.txt desempenha um papel crucial na gestão do acesso dos motores de busca ao conteúdo do seu site. Certifique-se de configurá-lo corretamente para otimizar a indexação e a visibilidade nos resultados de pesquisa.