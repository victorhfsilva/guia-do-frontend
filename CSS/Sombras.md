# Sombras

## Sombra de Caixa (Box Shadow)

A propriedade `box-shadow` permite adicionar sombras a elementos de caixa, como divs, botões e caixas de texto. Ela segue a seguinte sintaxe:

```css
box-shadow: h-shadow v-shadow blur spread color inset;
```

- `h-shadow`: Deslocamento horizontal da sombra (positivo para direita, negativo para esquerda).
- `v-shadow`: Deslocamento vertical da sombra (positivo para baixo, negativo para cima).
- `blur`: Desfoque da sombra (opcional).
- `spread`: Expansão ou contração da sombra (opcional).
- `color`: Cor da sombra.
- `inset`: Opcional, cria uma sombra interna se presente.

Exemplo:

```css
box-shadow: 5px 5px 10px #888888;
```

## Sombra de Texto (Text Shadow)

A propriedade `text-shadow` permite adicionar sombras a texto dentro de elementos HTML. Ela segue a seguinte sintaxe:

```css
text-shadow: h-shadow v-shadow blur color;
```

- `h-shadow`: Deslocamento horizontal da sombra de texto (positivo para direita, negativo para esquerda).
- `v-shadow`: Deslocamento vertical da sombra de texto (positivo para baixo, negativo para cima).
- `blur`: Desfoque da sombra de texto (opcional).
- `color`: Cor da sombra de texto.

Exemplo:

```css
text-shadow: 2px 2px 4px #000000;
```

## Sombra Difusa (Drop Shadow)

A propriedade `filter` com o valor `drop-shadow` cria uma sombra difusa em um elemento. Ela segue a seguinte sintaxe:

```css
filter: drop-shadow(h-shadow v-shadow blur color);
```

- `h-shadow`: Deslocamento horizontal da sombra (positivo para direita, negativo para esquerda).
- `v-shadow`: Deslocamento vertical da sombra (positivo para baixo, negativo para cima).
- `blur`: Desfoque da sombra (opcional).
- `color`: Cor da sombra.

Exemplo:

```css
filter: drop-shadow(5px 5px 10px #888888);
```
