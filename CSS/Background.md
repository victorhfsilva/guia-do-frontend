# Backgrounds em CSS

## Propriedade `background-image`

- A propriedade `background-image` permite adicionar uma imagem de plano de fundo a um elemento.

   Exemplo:
   ```css
   .elemento {
     background-image: url('imagem.jpg');
   }
   ```

## Propriedade `background-repeat`

- A propriedade `background-repeat` controla como a imagem de fundo é repetida ao longo do elemento.

   - `repeat`: A imagem é repetida tanto na horizontal quanto na vertical (padrão).
   - `repeat-x`: A imagem é repetida apenas horizontalmente.
   - `repeat-y`: A imagem é repetida apenas verticalmente.
   - `no-repeat`: A imagem não é repetida.
   - `space`: Distribui as imagens homogeneamente, preenchendo o espaços livres com espaços em brancos. Não permite que as imagens sejam cortadas.  
   - `round`: Distribui as imagens homogeneamente, não permite o corte das imagens, mas tbm não preenche o espaço livre com espaços em branco, em vez disso ela distorce as imagens caso necessário.

   Exemplo:
   ```css
   .elemento {
     background-image: url('imagem.jpg');
     background-repeat: no-repeat;
   }
   ```

## Propriedade `background-size`

- A propriedade `background-size` define o tamanho da imagem de plano de fundo em relação ao elemento.

   - `auto`: Tamanho automático (padrão).
   - `cover`: A imagem é dimensionada para cobrir todo o elemento, mantendo a proporção.
   - `contain`: A imagem é dimensionada para caber inteiramente dentro do elemento, mantendo a proporção.
   - `valor`: Pode ser um valor específico, como `100px`, `50%`, `20px 30px`, `20px 100%`, etc.

   Exemplo:
   ```css
   .elemento {
     background-image: url('imagem.jpg');
     background-size: cover;
   }
   ```

## Propriedade `background-position`

### 1. Posições Básicas

- Como definir a posição do plano de fundo usando palavras-chave, como `top`, `right`, `bottom`, `left`, `center`, etc.

   ```css
   background-position: top center;
   ```

### 2. Posições Personalizadas

- Usar coordenadas personalizadas (porcentagens ou valores em pixels) para posicionar o plano de fundo.

   ```css
   background-position: 20% 30%;
   ```

## Propriedade `background-attachment`

### 1. Fixed e Scroll

- Controlar se o plano de fundo rola com o restante do conteúdo da página (`scroll`) ou se permanece fixo na janela (`fixed`).

   ```css
   background-attachment: fixed;
   ```

### 2. Local

- Rola junto com o conteúdo do elemento, não da página.

   ```css
   background-attachment: local;
   ```

## Propriedade `background-origin`

### 1. Content Box

- Especificar que o plano de fundo deve começar a partir das bordas da caixa de conteúdo. Não preenche o padding.

   ```css
   background-origin: content-box;
   ```

### 2. Padding Box

- Definir que o plano de fundo deve começar a partir do limite interno das bordas da caixa de preenchimento (padding box).

   ```css
   background-origin: padding-box;
   ```

### 3. Border Box

- O plano de fundo deve começar a partir do limite externo das bordas da caixa de preenchimento.

   ```css
   background-origin: border-box;
   ```

## Propriedade `linear-gradient`

### 1. Sintaxe Básica

- Exemplo da sintaxe básica para criar um gradiente linear:

   ```css
   background: linear-gradient(to right, red, blue);
   ```

### 2. Direções

- Como especificar a direção do gradiente linear usando palavras-chave como `to top`, `to right`, `to bottom`, `to left`, etc.

   ```css
   background: linear-gradient(to top, red, blue);
   ```

### 3. Cores

- Adicionar mais cores ao gradiente linear para criar transições suaves.

   ```css
   background: linear-gradient(to right, red, yellow, green, blue);
   ```

### 4. Ângulos

- Usar ângulos em graus para definir a direção do gradiente linear.

   ```css
   background: linear-gradient(45deg, red, blue);
   ```

## Propriedade `radial-gradient``

### 1. Sintaxe Básica

- Exemplo da sintaxe básica para criar um gradiente radial:

   ```css
   background: radial-gradient(circle, red, blue);
   ```

### 2. Formas

- Como especificar a forma do gradiente radial usando palavras-chave como `circle`, `ellipse`, etc.

   ```css
   background: radial-gradient(ellipse, red, blue);
   ```

### 3. Posições

- Controlar a posição do centro do gradiente radial usando coordenadas.

   ```css
   background: radial-gradient(at 50% 50%, red, blue);
   ```

### 4. Tamanhos

- Definir o tamanho do gradiente radial com valores como `farthest-corner`, `closest-corner`, `farthest-side`, `closest-side`, etc.

   ```css
   background: radial-gradient(circle farthest-corner, red, blue);
   ```

## Propriedade `repeating-linear-gradient``

### 1. Repetição

- Como criar gradientes lineares que se repetem em um elemento.

   ```css
   background: repeating-linear-gradient(to right, red, blue 20px);
   ```

### 2. Intervalos

- Controlar os intervalos entre cada repetição do gradiente linear.

   ```css
   background: repeating-linear-gradient(to right, red 0, blue 20px);
   ```

### 3. Cores

- Adicionar cores para definir a sequência de cores que se repetirá.

   ```css
   background: repeating-linear-gradient(to right, red 0, green 10px, blue 20px);
   ```

### 4. Direções

- Especificar a direção do gradiente linear repetido da mesma forma que no `linear-gradient`.

   ```css
   background: repeating-linear-gradient(to top, red, blue 20px);
   ```


## Propriedade background-blend-mode

A propriedade `background-blend-mode` permite que você defina como as imagens de plano de fundo (ou cores) se mesclam entre si e com o conteúdo do elemento, criando efeitos de mistura interessantes. Ela é especialmente útil quando você tem múltiplas imagens de plano de fundo sobrepostas.

### Valores Possíveis

- `normal`: Esse é o valor padrão. As imagens de plano de fundo não são mescladas; cada imagem é desenhada conforme sua ordem no CSS.

   ```css
   background-blend-mode: normal;
   ```

- `multiply`: As cores das imagens de plano de fundo são multiplicadas, criando um efeito de escurecimento.

   ```css
   background-blend-mode: multiply;
   ```

- `screen`: As cores das imagens de plano de fundo são invertidas, multiplicadas e depois invertidas novamente, criando um efeito de clareamento.

   ```css
   background-blend-mode: screen;
   ```

- `overlay`: O efeito final é uma combinação do modo `multiply` e `screen`, criando um efeito de contraste.

   ```css
   background-blend-mode: overlay;
   ```

- `darken`: O resultado é a cor mais escura entre as imagens de plano de fundo.

   ```css
   background-blend-mode: darken;
   ```

- `lighten`: O resultado é a cor mais clara entre as imagens de plano de fundo.

   ```css
   background-blend-mode: lighten;
   ```

- `color-dodge`: As cores das imagens de plano de fundo são clareadas, criando um efeito de realce.

   ```css
   background-blend-mode: color-dodge;
   ```

- `color-burn`: As cores das imagens de plano de fundo são escurecidas, criando um efeito de sombreamento.

   ```css
   background-blend-mode: color-burn;
   ```

- `difference`: O efeito é baseado na diferença entre as cores das imagens de plano de fundo.

   ```css
   background-blend-mode: difference;
   ```

- `exclusion`: O efeito é semelhante ao `difference`, mas com um resultado mais sutil.

   ```css
   background-blend-mode: exclusion;
   ```

- `hue`: O resultado é a cor da primeira imagem de plano de fundo, com a luminosidade e saturação da segunda imagem.

   ```css
   background-blend-mode: hue;
   ```

- `saturation`: O resultado é a cor da primeira imagem de plano de fundo, com a luminosidade e tonalidade da segunda imagem.

   ```css
   background-blend-mode: saturation;
   ```

- `color`: O resultado é a cor da primeira imagem de plano de fundo, com a luminosidade da segunda imagem.

   ```css
   background-blend-mode: color;
   ```

- `luminosity`: O resultado é a cor da primeira imagem de plano de fundo, com a saturação e tonalidade da segunda imagem.

   ```css
   background-blend-mode: luminosity;
   ```

### Exemplo de Uso

Neste exemplo, as imagens de plano de fundo serão multiplicadas, criando um efeito de escurecimento onde as duas imagens se sobrepõem.

```css
.element {
  background-image: url('imagem1.jpg'), url('imagem2.jpg');
  background-blend-mode: multiply;
}
```

Já neste, a imagem será mesclada com a cor laranja utilizando o lighten.

```css
.element {
    background-color: orange;
    background-image: url('imagem.png');
    background-blen-mode: lighten;
}
```


