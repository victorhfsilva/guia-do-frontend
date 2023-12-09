# Elemento `<img>`

- No caso de um elemento `<img>`, você pode aplicar as propriedades `object-fit` e `object-position:

   Exemplo:
   ```css
   img {
     object-fit: cover;
     object-position: top center;
   }
   ```

### 1. Propriedade `object-fit`

- A propriedade `object-fit` controla como a imagem é dimensionada e posicionada dentro de um elemento.

   - `fill`: A imagem preenche completamente o elemento, possivelmente distorcendo a proporção.
   - `contain`: A imagem é dimensionada para caber dentro do elemento, mantendo a proporção e preenchendo o espaço restante com espaços em branco.
   - `cover`: A imagem é dimensionada para cobrir o elemento, mantendo a proporção e cortando se necessário.
   - `none`: A imagem mantém seu tamanho original, cortando o excesso, se necessário.
   - `scale-down`: A imagem é dimensionada para ser a menor possível, mantendo a proporção e preenchendo o espaço restante com espaços em branco (modo "contain" ou "none", o menor).

   Exemplo:
   ```css
   .elemento img {
     object-fit: cover;
   }
   ```

### 2. Propriedade `object-position`

- A propriedade `object-position` controla a posição da imagem dentro do elemento.

   - `top`, `right`, `bottom`, `left`: Posições específicas para alinhar a imagem.
   - `center`: O centro do elemento (padrão).
   - Valores em porcentagem ou unidades, como `50% 20%`.

   Exemplo:
   ```css
   .elemento img {
     object-position: top right;
   }
   ```
