# **Fontes em CSS**

## Personalizando Fontes

```css
font-family: Arial, sans-serif; /* Define a fonte preferida e as alternativas */
```

Um site muito interessante para explorar combinações de fontes é o [Fontpair](https://www.fontpair.co/).

## Aplicando Fontes Personalizadas com @font-face

```css
@font-face {
  font-family: 'MinhaFonte';
  src: url('minha-fonte.woff2') format('woff2');
  /* Outros formatos de fonte e variações de peso/style podem ser adicionados */
}

classe {
  font-family: 'MinhaFonte', sans-serif;
}
```

## Aplicando Fontes Personalizadas com @import url()

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
/* Use a fonte importada como qualquer outra fonte */
```

## Alterando o Tamanho com font-size

```css
font-size: 16px; /* Tamanho em pixels */
font-size: 1rem; /* Tamanho relativo à raiz (root) */
font-size: 1.2em; /* Tamanho relativo ao tamanho atual */
```

## Alterando o Estilo com font-style

```css
font-style: italic; /* Itálico */
font-style: oblique; /* Versão levemente inclinada */
font-style: normal; /* Normal (padrão) */
```

## Alterando a Espessura com font-weight

```css
font-weight: bold; /* Negrito */
font-weight: 600; /* Números de 100 (mais leve) a 900 (mais pesado) */
font-weight: normal; /* Normal (padrão) */
```

## Propriedade font-variant

```css
font-variant: small-caps; /* Exibe as letras minúsculas como maiúsculas pequenas */
font-variant: normal; /* Normal (padrão) */
```

## Propriedade font-stretch

```css
font-stretch: expanded; /* Estica a largura das letras */
font-stretch: condensed; /* Comprime a largura das letras */
font-stretch: normal; /* Normal (padrão) */
```

## Propriedade line-height

```css
line-height: 1.5; /* Espaçamento entre linhas */
line-height: 120%; /* Espaçamento relativo ao tamanho da fonte */
```