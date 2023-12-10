## Aspas

Em JavaScript, você pode criar strings usando aspas duplas (`"`), aspas simples (`'`), ou crases (acentos graves, `` ` ``). Cada tipo de citação tem suas próprias características e uso adequado. Aqui estão as diferenças entre eles:

### Aspas Duplas (" ")

- Strings criadas com aspas duplas são delimitadas por `"`.

- Você pode usar aspas simples dentro de strings delimitadas por aspas duplas sem escapá-las.

   ```javascript
   const stringComAspasDuplas = "Isso é uma string com 'aspas simples' dentro.";
   ```

- As strings com aspas duplas são úteis quando você deseja incluir aspas simples dentro da string sem precisar escapá-las.

### Aspas Simples (' ')

- Strings criadas com aspas simples são delimitadas por `'`.

- Você pode usar aspas duplas dentro de strings delimitadas por aspas simples sem escapá-las.

   ```javascript
   const stringComAspasSimples = 'Isso é uma string com "aspas duplas" dentro.';
   ```

- As strings com aspas simples são úteis quando você deseja incluir aspas duplas dentro da string sem precisar escapá-las.

### Crases (\` \`)

- Strings criadas com crases são delimitadas por \` \` (acentos graves).

- As crases permitem a interpolação de variáveis diretamente na string usando `${}`.

   ```javascript
   const nome = "João";
   const stringComCrases = `Olá, ${nome}!`;
   ```

- Você pode criar strings de várias linhas sem a necessidade de caracteres de escape.

   ```javascript
   const stringMultilinha = `
   Esta é uma string
   com várias linhas.
   `;
   ```

- As strings com crases são ideais quando você precisa criar strings com interpolação ou strings multilinhas.

### Escolhendo o Tipo Certo de Cotação

- Use aspas duplas ou aspas simples quando precisar criar strings simples sem interpolação ou várias linhas.

- Use crases quando precisar de interpolação de variáveis ou desejar criar strings multilinhas.

Lembre-se de escolher o tipo de cotação apropriado com base nas necessidades do seu código. As aspas duplas, aspas simples e crases são todas válidas em JavaScript e oferecem flexibilidade para diferentes situações.
