# Grid Layout em CSS

O Grid Layout é um sistema poderoso de posicionamento de elementos em CSS que permite criar layouts complexos de maneira mais eficiente e flexível. Ele divide o espaço em linhas e colunas, tornando o design de páginas da web mais preciso. Aqui estão alguns conceitos e propriedades essenciais do Grid Layout:

## Estrutura Básica do Grid

### Definindo um Container de Grid

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* Define 3 colunas de tamanho igual */
  grid-template-rows: auto auto; /* Define 2 linhas de tamanho automático */
}
```

### Definindo o Grid Implicitamente

O Grid pode ser definido implicitamente pelo conteúdo.

```css
.container {
  display: grid;
  grid-auto-columns: 1fr; /* Colunas implícitas têm tamanho igual */
  grid-auto-rows: minmax(100px, auto); /* Linhas implícitas têm tamanho mínimo de 100px e tamanho automático */
}
```

## Tamanhos Mínimos e Máximos de Faixas

### `minmax()`

```css
.container {
  grid-template-columns: minmax(100px, 1fr); /* Coluna com tamanho mínimo de 100px e máximo de 1fr */
}
```

## Shorthand `grid-template`

```css
.container {
  grid-template: 1fr 2fr / 100px 1fr; /* 2 linhas e 2 colunas com tamanhos especificados */
}
```

## Alinhamento

### `justify-items` e `align-items`

A propriedade `justify-items` é usada para alinhar os itens horizontalmente dentro de um contêiner. Aqui estão algumas opções:

- `center`: Alinha os itens horizontalmente no centro.
- `start`: Alinha os itens horizontalmente no início.
- `end`: Alinha os itens horizontalmente no final.
- `stretch`: Estica os itens horizontalmente para preencher o contêiner.
- `space-around`: Distribui o espaço extra uniformemente entre os itens horizontalmente.
- `space-between`: Distribui o espaço extra uniformemente, colocando o primeiro item no início e o último no final.

A propriedade `align-items` é usada para alinhar os itens verticalmente. Aqui estão algumas opções:

- `start`: Alinha os itens verticalmente no início.
- `center`: Alinha os itens verticalmente no centro.
- `end`: Alinha os itens verticalmente no final.
- `stretch`: Estica os itens verticalmente para preencher o contêiner.
- `baseline`: Alinha os itens verticalmente pela linha de base (quando aplicável).

```css
.container {
  justify-items: center; /* Alinha os itens horizontalmente no centro */
  align-items: start; /* Alinha os itens verticalmente no início */
}
```

### `justify-content` e `align-content`

A propriedade `justify-content` é usada para alinhar as linhas (ou colunas) dentro de um contêiner. Aqui estão algumas opções:

- `start`: Alinha as linhas no início do contêiner.
- `center`: Alinha as linhas no centro do contêiner.
- `end`: Alinha as linhas no final do contêiner.
- `space-between`: Distribui o espaço extra uniformemente entre as linhas, colocando a primeira no início e a última no final.
- `space-around`: Distribui o espaço extra uniformemente entre as linhas.
- `space-evenly`: Distribui o espaço extra uniformemente entre as linhas, incluindo antes da primeira e depois da última.
- `stretch`: Estica as linhas para preencher o contêiner.

A propriedade `align-content` é usada para alinhar as colunas (ou linhas) verticalmente. Aqui estão algumas opções:

- `start`: Alinha as colunas no início do contêiner.
- `center`: Alinha as colunas no centro do contêiner.
- `end`: Alinha as colunas no final do contêiner.
- `space-between`: Distribui o espaço extra uniformemente entre as colunas, colocando a primeira no início e a última no final.
- `space-around`: Distribui o espaço extra uniformemente entre as colunas.
- `space-evenly`: Distribui o espaço extra uniformemente entre as colunas, incluindo antes da primeira e depois da última.
- `stretch`: Estica as colunas para preencher o contêiner.

```css
.container {
  justify-content: space-around; /* Distribui o espaço extra uniformemente nas colunas */
  align-content: space-between; /* Distribui o espaço extra uniformemente nas linhas */
}
```

## Posicionamento de Itens

O posicionamento de itens em um grid é crucial para criar layouts complexos e responsivos. As propriedades `grid-row` e `grid-column` especificam as linhas e colunas que um item do grid deve ocupar.

### `grid-row` e `grid-column`

```css
.item {
  grid-column: 2 / 4; /* O item ocupa da coluna 2 à coluna 4 */
  grid-row: 1 / 3; /* O item ocupa da linha 1 à linha 3 */
}
```

- `grid-column`: Define a faixa de colunas que o item deve ocupar no grid.
- `grid-row`: Define a faixa de linhas que o item deve ocupar no grid.

No exemplo acima, o item ocupa as colunas da 2ª à 4ª e as linhas da 1ª à 3ª.

### `justify-self` e `align-self`

Além de posicionar um item no grid, é possível ajustar sua posição dentro do espaço que ele ocupa usando `justify-self` e `align-self`.

```css
.item {
  justify-self: end; /* Alinha o item no final da coluna */
  align-self: center; /* Alinha o item no centro da linha */
}
```

- `justify-self`: Alinha o item horizontalmente dentro de seu espaço no grid.
- `align-self`: Alinha o item verticalmente dentro de seu espaço no grid.

No exemplo acima, o item é alinhado no final da coluna e no centro da linha.

### `place-self`

A propriedade `place-self` é uma forma concisa de definir tanto o alinhamento horizontal quanto o vertical em uma única declaração.

```css
.item {
  place-self: start end; /* Alinha o item no início da coluna e no final da linha */
}
```

- `place-self`: Define o alinhamento horizontal e vertical do item em uma única declaração.

Neste exemplo, o item é alinhado no início da coluna e no final da linha. A utilização de `place-self` pode simplificar a definição de posicionamento em alguns casos.


## `gap`

A propriedade `gap` no Grid Layout é usada para definir o espaço entre as linhas e colunas em um grid. É uma maneira eficiente de adicionar espaçamento uniforme e consistente entre os elementos em um layout. Você pode definir um valor para as linhas, colunas ou ambos. Por exemplo:

```css
.container {
  display: grid;
  grid-gap: 10px; /* Define um espaçamento de 10px entre todas as linhas e colunas */
}
```

Ou você pode definir valores separados para linhas e colunas:

```css
.container {
  display: grid;
  row-gap: 20px; /* Define um espaçamento de 20px entre as linhas */
  column-gap: 10px; /* Define um espaçamento de 10px entre as colunas */
}
```

O uso de `gap` simplifica o código e oferece um método consistente para adicionar espaçamento em seu layout de grid.

O Grid Layout oferece controle avançado sobre o posicionamento de elementos em layouts de página, permitindo a criação de designs complexos com facilidade. Experimente e ajuste as propriedades para atender às necessidades específicas de seu projeto.