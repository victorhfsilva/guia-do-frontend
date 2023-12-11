# Cookies em JavaScript

Os cookies são pequenos arquivos de texto armazenados no navegador do usuário. Eles são amplamente utilizados para armazenar informações temporárias ou de sessão no lado do cliente. Aqui está um guia rápido sobre como usar cookies em JavaScript:

## **Configuração de um Cookie:**

- Para definir um cookie, você usa a propriedade `document.cookie`. A string do cookie geralmente tem a forma "chave=valor".

```javascript
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2023 12:00:00 UTC; path=/";
```

- `expires`: Define a data de expiração do cookie. Após essa data, o cookie é automaticamente removido.

- `path`: Especifica o diretório para o qual o cookie está disponível. O valor "/" torna o cookie disponível em todo o site.

## **Recuperação de um Cookie:**

Para recuperar cookies, você pode analisar a propriedade `document.cookie` e extrair os valores desejados.

```javascript
const cookies = document.cookie.split("; ");
for (const cookie of cookies) {
  const [key, value] = cookie.split("=");
  console.log(`${key}: ${value}`);
}
```

## **Exclusão de um Cookie:**

- Para excluir um cookie, você pode definir seu valor como vazio e definir uma data de expiração passada.

```javascript
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/";
```

## **Observações Importantes:**

- **Segurança:**
  - Evite armazenar informações sensíveis em cookies, pois eles podem ser acessados e modificados pelo usuário.

- **Capacidade de Armazenamento:**
  - O tamanho total dos cookies por domínio é limitado (geralmente alguns kilobytes).

- **Protocolo Seguro (HTTPS):**
  - Cookies seguros (definidos com a flag "Secure") só são enviados via HTTPS.

- **Domínio e Caminho:**
  - Os cookies são específicos para um domínio e caminho, e só podem ser acessados por páginas dentro desses limites.

- **Número de Cookies:**
  - Há um limite para o número de cookies que um navegador pode armazenar por domínio.

- **SameSite:**
  - A propriedade SameSite pode ser usada para restringir quando os cookies são enviados junto com as solicitações. 

### **Exemplo de Configuração com SameSite:**

```javascript
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2023 12:00:00 UTC; path=/; SameSite=Strict";
```

Lembre-se de considerar as implicações de segurança e privacidade ao usar cookies e seguir as práticas recomendadas para garantir um uso adequado.