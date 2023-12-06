# Bordas em CSS

As bordas são propriedades importantes para estilizar elementos HTML e são amplamente usadas para adicionar efeitos visuais, divisões e ênfases aos elementos. As bordas são definidas por várias propriedades que controlam seu tamanho, estilo, cor e outros aspectos.

## 1. **Tamanho da Borda (border-width)**

   - Define a largura da borda. Pode ser definida em pixels, em, ou com valores predefinidos.

   ```css
   border-width: 2px; /* Largura de 2 pixels */
   ```

## 2. **Estilo da Borda (border-style)**

   - Define o estilo da borda, como sólido, tracejado, pontilhado, duplo, entre outros.

   ```css
   border-style: solid; /* Borda sólida */
   ```

   Aqui está uma lista de estilos de bordas em CSS:

1. solid
2. dotted
3. dashed
4. double
5.  groove
6. ridge
7. inset
8. outset
9. none
10. hidden

## 3. **Cor da Borda (border-color)**

   - Define a cor da borda. Pode ser um nome de cor, código hexadecimal, RGB ou RGBA.

   ```css
   border-color: #ff0000; /* Cor vermelha */
   ```

## 4. **Propriedade Border**

   - Uma forma abreviada de definir todas as propriedades de borda (largura, estilo e cor) em uma única declaração.

   ```css
   border: 2px solid #ff0000; /* Largura, estilo e cor da borda em uma linha */
   ```

## 5. **Border-Radius**

   - Define o raio das bordas de um elemento, criando cantos arredondados.

   ```css
   border-radius: 10px; /* Cantos arredondados com raio de 10 pixels */
   ```

## 6. **Border Image Source**

   - Define uma imagem como borda em torno de um elemento.

   ```css
   border-image-source: url('border.png'); /* Define uma imagem como borda */
   ```

## 7. **Border Image Slice**

   - O `border-image-slice` é uma propriedade CSS que define como uma imagem de borda é dividida e ajustada para preencher a borda de um elemento. Ela é usada em conjunto com a propriedade `border-image-source`.

   ```css
   border-image-slice: 30 fill;
   ```

### **Opções de Border Image Slice**

Existem quatro valores que podem ser definidos para `border-image-slice`:

1. **Número Único:** Um número único especifica a largura da área de corte em todas as quatro bordas da imagem. Por exemplo, `border-image-slice: 20px;` irá definir uma área de corte de 20 pixels em todas as bordas.

2. **Dois Números:** Dois números especificam a largura da área de corte nas bordas horizontal e vertical da imagem, nesta ordem. Por exemplo, `border-image-slice: 10px 20px;` irá definir uma área de corte de 10 pixels nas bordas horizontais e 20 pixels nas bordas verticais.

3. **Quatro Números:** Quatro números especificam a largura da área de corte nas bordas superior, direita, inferior e esquerda da imagem, nesta ordem. Por exemplo, `border-image-slice: 10px 20px 15px 25px;` irá definir uma área de corte de 10 pixels na borda superior, 20 pixels na borda direita, 15 pixels na borda inferior e 25 pixels na borda esquerda.

4. **Fill:** A palavra-chave `fill` é usada para indicar que a imagem de borda deve preencher completamente a área da borda sem corte.

A propriedade `border-image-slice` é útil para criar bordas personalizadas com imagens, permitindo um controle preciso sobre como a imagem é dimensionada e repetida nas bordas dos elementos.

## 8. **Border Image Width**

   - Define a largura da imagem da borda.

   ```css
   border-image-width: 10px;
   ```

## 9. **Border Image Repeat**

   - A propriedade `border-image-repeat` em CSS permite controlar como uma imagem de borda é repetida ao longo das bordas de um elemento. Ela funciona em conjunto com a propriedade `border-image-source`.

   ```css
   border-image-repeat: round;
   ```

### **Opções de Border Image Repeat**

Existem quatro valores que podem ser atribuídos à `border-image-repeat`:

1. **stretch:** Este é o valor padrão. Ele estica a imagem de borda para preencher a área da borda, o que pode resultar em distorção da imagem se a proporção da imagem não corresponder à proporção da borda.

2. **repeat:** A imagem de borda é repetida ao longo das bordas, sem esticamento. Se a imagem for menor do que a área da borda, ela será repetida até preencher a área.

3. **round:** A imagem de borda é repetida até que a área da borda seja preenchida, mas sem esticamento. Se a imagem não couber perfeitamente, ela será dimensionada para que uma quantidade inteira de imagens caiba na área da borda sem deixar espaços vazios.

4. **space:** A imagem de borda é repetida até que a área da borda seja preenchida, mas sem esticamento. Se a imagem não couber perfeitamente, ela será dimensionada para que haja espaços iguais entre as imagens repetidas.

Essas opções de repetição de imagem de borda permitem um controle preciso sobre como a imagem é tratada ao longo das bordas de um elemento, ajudando a criar efeitos visuais interessantes em elementos com bordas personalizadas.

#### 10. **Border Image Outset**

   - Define o afastamento da imagem da borda.

   ```css
   border-image-outset: 10px 20px; /* Define afastamentos horizontal e vertical */
   ```
