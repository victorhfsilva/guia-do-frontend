# Google Hacking

## **Definição:**
- Google Hacking é uma técnica que utiliza operadores de pesquisa avançados no Google para encontrar informações sensíveis e identificar vulnerabilidades em sites e sistemas online.

## **Operadores de Pesquisa:**

### **`intitle`**: 
- Restringe os resultados àqueles com palavras-chave específicas no título.
- Exemplo: `intitle:"Index of" password`

### **`inurl`**: 
- Filtra resultados que contenham uma determinada string na URL.
- Exemplo: `inurl:admin`

### **`filetype`**: 
- Limita a pesquisa a arquivos de um tipo específico.
- Exemplo: `filetype:pdf`

###  `intext`:
- Procura por informações no código-fonte HTML
- Exemplo: `intext:password`

### `site`:
- Busca um site em específico.
- Exemplo: `site:wikipedia.org`

### `related`:
- Busca sites relacionados.
- Exemplo: `related:wikipedia.org`

### `cache`:
- Busca os sites salvos em cache do Google.
- Exemplo: `cache:wikipedia.org`

### `""`: 
- Busca por um padrão exato
- Exemplo: `"Wikipedia"`

### `+`:
- Busca por mais de uma palavra
- Exemplo: `jaguar + car`

### `-`:
- Exclui palavras da busca
- Exemplo: `jaguar speed -car`

### `OR`: 
- Combina duas palavras na busca
- Exemplo: `jaguar OR car`

### `imagesize`:
- Busca o tamanho da imagem.
- Exemplo: `imagesize:320x320`

### `@`:
- Busca em redes sociais
- Exemplo: `@wikipedia`

### `#`:
- Busca por hashtags
- Exemplo: `#wiki`

### `$`:
- Busca por um preço específico.
- Exemplo: `tênis $390`

### `..`:
- Busca por um intervalo de preços.
- Exemplo: `tênis $120..$540`


## **Objetivos do Google Hacking:**
1. **Identificação de Informações Sensíveis:**
   - Busca por documentos, senhas, e outras informações sensíveis publicamente disponíveis.

2. **Localização de Páginas de Login e Administração:**
   - Encontrar URLs de páginas de login e administração que podem ser alvos para ataques.

3. **Descoberta de Vulnerabilidades:**
   - Identificar possíveis pontos de entrada para ataques cibernéticos explorando falhas de segurança.

## **Riscos para a Segurança:**
1. **Exposição de Informações Confidenciais:**
   - Revelação não intencional de dados confidenciais, como credenciais de login ou informações sensíveis.

2. **Identificação de Pontos Fracos:**
   - Facilita a identificação de vulnerabilidades, possibilitando ataques mais direcionados.

## **Prevenção:**
1. **Configuração Adequada do robots.txt:**
   - Instrua os motores de busca sobre quais partes do site não devem ser indexadas.

2. **Validação de Entrada:**
   - Implemente verificações rigorosas para evitar injeções de código por meio de dados de entrada.

3. **Autenticação e Acesso Restrito:**
   - Proteja informações sensíveis por meio de autenticação e acesso restrito.

4. **Monitoramento Contínuo:**
   - Faça monitoramento regular para identificar potenciais exposições de informações sensíveis.

## Mais Recursos

- [Google Hacking Database](https://www.exploit-db.com/google-hacking-database): é um projeto que compila uma série de *dorks* conhecidos.

## **Conclusão:**

O Google Hacking destaca a importância da segurança cibernética e da conscientização para prevenir explorações indevidas de informações. Adotar práticas proativas de segurança é essencial para proteger dados sensíveis e manter a integridade online.