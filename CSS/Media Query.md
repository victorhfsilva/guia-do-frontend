# Media Queries em CSS

As Mídia Queries são uma técnica essencial para criar layouts responsivos em CSS. Elas permitem que você aplique estilos específicos a diferentes dispositivos ou tamanhos de tela. 

## Sintaxe Básica

As Mídia Queries são usadas dentro de blocos `@media` e têm a seguinte sintaxe básica:

```css
@media tipo-de-midia and (condição) {
    /* Estilos para a mídia específica */
}
```

- `tipo-de-midia`: Define o tipo de mídia (por exemplo, `screen`, `print`, `all`).
- `condição`: Define a condição que deve ser atendida para aplicar os estilos.

## Exemplos de Tipos de Mídia

### `screen`

- Estilos aplicados quando a página é exibida na tela.

```css
@media screen {
    /* Estilos para tela */
}
```

### `print`

- Estilos aplicados quando a página é impressa.

```css
@media print {
    /* Estilos para impressão */
}
```

### `all`

- Estilos aplicados em todos os tipos de mídia.

```css
@media all {
    /* Estilos para todos os tipos de mídia */
}
```

### `speech`

- O tipo `speech` é usado para estilos de saída de fala, geralmente para leitores de tela.

```css
@media speech {
  /* Estilos aplicados à saída de fala, como leitores de tela */
}
```

### `not`

- O operador `not` permite negar um tipo de mídia para aplicar estilos a todos os tipos, exceto o especificado.

```css
@media not screen {
  /* Estilos aplicados a todos os tipos de mídia, exceto dispositivos de tela */
}
```

### `only`

- A palavra-chave `only` é usada para evitar que navegadores mais antigos apliquem regras que não compreendem.

```css
@media only screen and (max-width: 768px) {
  /* Estilos aplicados a dispositivos de tela com largura máxima de 768px */
}
```

## Exemplos de Condições

### Largura da Tela (`max-width` e `min-width`)

- Aplicar estilos quando a largura da tela estiver dentro de um intervalo específico.

```css
@media screen and (max-width: 768px) {
    /* Estilos para telas menores ou iguais a 768px de largura */
}

@media screen and (min-width: 1024px) {
    /* Estilos para telas maiores ou iguais a 1024px de largura */
}
```

### Orientação da Tela (`orientation`)

- Aplicar estilos com base na orientação da tela (retrato ou paisagem).

```css
@media screen and (orientation: portrait) {
    /* Estilos para orientação retrato */
}

@media screen and (orientation: landscape) {
    /* Estilos para orientação paisagem */
}
```

## Media Features em CSS

As Media Features são parte essencial das Media Queries em CSS, permitindo que você aplique estilos com base nas características do dispositivo ou da tela. Aqui estão algumas das media features mais úteis:

### `width`

```css
@media (max-width: 768px) {
  /* Estilos aplicados em telas com largura máxima de 768px */
}
```

A media feature `width` permite aplicar estilos com base na largura da tela.

### `height`

```css
@media (min-height: 600px) {
  /* Estilos aplicados em telas com altura mínima de 600px */
}
```

A media feature `height` permite aplicar estilos com base na altura da tela.

### `orientation`

```css
@media (orientation: landscape) {
  /* Estilos aplicados em telas no modo paisagem */
}
```

A media feature `orientation` permite aplicar estilos com base na orientação da tela (retrato ou paisagem).

### `aspect-ratio`

```css
@media (aspect-ratio: 16/9) {
  /* Estilos aplicados em telas com relação de aspecto de 16:9 */
}
```

A media feature `aspect-ratio` permite aplicar estilos com base na relação de aspecto da tela.

### `color`

```css
@media (min-color: 256) {
  /* Estilos aplicados em telas com suporte a cores de 256 ou mais */
}
```

A media feature `color` permite aplicar estilos com base na capacidade de cor da tela.

### `hover`

```css
@media (hover: hover) {
  /* Estilos aplicados quando o dispositivo suporta interações hover (ex: mouse) */
}
```

A media feature `hover` permite aplicar estilos com base na presença de interações hover (como mouse).

### `resolution`

```css
@media (min-resolution: 300dpi) {
  /* Estilos aplicados em telas com resolução mínima de 300 dpi */
}
```

A media feature `resolution` permite aplicar estilos com base na resolução da tela.

### `pointer`

```css
@media (pointer: coarse) {
  /* Estilos aplicados em dispositivos com interação limitada (ex: tela sensível ao toque) */
}
```

A media feature `pointer` permite aplicar estilos com base no tipo de dispositivo de entrada.

### `any-pointer`

```css
@media (any-pointer: fine) {
  /* Estilos aplicados quando há pelo menos um dispositivo de entrada de alta precisão */
}
```

A media feature `any-pointer` permite aplicar estilos com base na presença de pelo menos um dispositivo de entrada de alta precisão.


## Operadores de Media Queries

- Use operadores para combinar e ajustar as condições das media queries. Exemplo: `@media (min-width: 768px) and (orientation: landscape) { /* estilos */ }`.

Aqui estão os operadores mais comuns:

### `and`

O operador `and` combina duas ou mais condições em uma media query. Todas as condições devem ser verdadeiras para que os estilos se apliquem.

### `or` (`,`)

O operador `or`, representado por uma vírgula `,`, permite que os estilos se apliquem se pelo menos uma das condições for verdadeira. Ele é usado para criar regras alternativas.

### `not`

O operador `not` nega uma condição, fazendo com que os estilos se apliquem quando a condição não é atendida.

## Exemplo de Uso

```css
/* Estilos padrão para dispositivos com tela grande */
body {
    font-size: 16px;
    background-color: #fff;
    color: #333;
}

/* Mídia Query para telas pequenas (até 768px de largura) */
@media screen and (max-width: 768px) {
    body {
        font-size: 14px;
        background-color: #f0f0f0;
    }
}
```

Neste exemplo, os estilos padrão são aplicados a dispositivos com tela grande, enquanto a Mídia Query ajusta o tamanho da fonte e a cor de fundo para telas menores (largura máxima de 768px).

## Breakpoints de Tamanhos de Tela

Ao desenvolver layouts responsivos, é comum utilizar breakpoints para ajustar o design da página de acordo com diferentes tamanhos de tela. Abaixo, apresentamos alguns breakpoints com base nos intervalos fornecidos:

### 1. **Dispositivos Móveis:**

```css
@media only screen and (max-width: 480px) {
  /* Estilos para dispositivos móveis */
}
```

- **Descrição:** Destinado a dispositivos com largura de tela entre 320 pixels e 480 pixels, abrangendo dispositivos móveis em geral.

### 2. **iPads e Tablets:**

```css
@media only screen and (min-width: 481px) and (max-width: 768px) {
  /* Estilos para iPads e tablets */
}
```

- **Descrição:** Direcionado a iPads e tablets, com larguras de tela entre 481 pixels e 768 pixels.

### 3. **Telas Pequenas e Laptops:**

```css
@media only screen and (min-width: 769px) and (max-width: 1024px) {
  /* Estilos para telas pequenas e laptops */
}
```

- **Descrição:** Apropriado para telas pequenas e laptops, abrangendo larguras de tela entre 769 pixels e 1024 pixels.

### 4. **Desktops e Telas Grandes:**

```css
@media only screen and (min-width: 1025px) and (max-width: 1200px) {
  /* Estilos para desktops e telas grandes */
}
```

- **Descrição:** Adequado para desktops e telas grandes, com larguras de tela entre 1025 pixels e 1200 pixels.

### 5. **Telas Muito Grandes e TVs:**

```css
@media only screen and (min-width: 1201px) {
  /* Estilos para telas muito grandes e TVs */
}
```

- **Descrição:** Aplicado a telas muito grandes, como desktops de alta resolução e TVs, com larguras de tela de 1201 pixels ou mais.

Esses breakpoints servem como referências cruciais para ajustar o layout da página, garantindo uma experiência de usuário consistente em uma variedade de dispositivos e tamanhos de tela, desde dispositivos móveis até telas grandes de TVs.