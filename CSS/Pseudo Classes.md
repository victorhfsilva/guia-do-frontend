# Pseudo Classes e Elementos em CSS

As pseudo-classes em CSS permitem selecionar elementos HTML com base em estados ou posições específicas. Elas são usadas para aplicar estilos a elementos que não podem ser selecionados apenas com seletores simples.

## Sintaxe Básica

As pseudo-classes são anexadas aos seletores de elementos para definir o estado ou a posição que deseja selecionar. A sintaxe básica é:

```css
seletor:pseudo-classe {
    propriedade: valor;
}
```

## Pseudo-classes de Estado

### `:hover`

- Seleciona um elemento quando o cursor do mouse está sobre ele.

```css
a:hover {
    color: blue;
}
```

### `:active`

- Seleciona um elemento quando ele é clicado.

```css
button:active {
    background-color: green;
}
```

### `:focus`

- Seleciona um elemento quando ele recebe foco (geralmente com tabulação ou clique).

```css
input:focus {
    border: 2px solid #ff0000;
}
```

### Pseudo-classe `:focus-within`

- Seleciona um elemento pai quando um de seus elementos filhos recebe foco.

```css
.formulario:focus-within {
    border: 2px solid #ff0000;
}
```

### `:checked`

- Seleciona elementos `<input>` do tipo `radio` ou `checkbox` que estão marcados.

```css
input[type="checkbox"]:checked {
    background-color: yellow;
}
```

## Pseudo-classes de Posição

### `:first-child`

- Seleciona o primeiro elemento filho de um pai.

```css
ul li:first-child {
    font-weight: bold;
}
```

### `:last-child`

- Seleciona o último elemento filho de um pai.

```css
ul li:last-child {
    font-style: italic;
}
```

### `:nth-child()`

- Seleciona elementos com base em sua posição em relação aos irmãos.

```css
ul li:nth-child(odd) {
    background-color: #f0f0f0;
}
```

## Pseudo-classes de Link

### `:link`

- Seleciona links não visitados.

```css
a:link {
    color: blue;
}
```

### `:visited`

- Seleciona links já visitados.

```css
a:visited {
    color: purple;
}
```

## Pseudo-classe lógicas

### `:not()`

- Seleciona elementos que não correspondem a um seletor específico.

```css
p:not(.destaque) {
    font-size: 16px;
}
```

### `:is`, `:where` e `:has`

- As pseudo-classes `:is`, `:where` e `:has` também podem ser usadas para criar seletores de condição.

```css
:is(h1, h2, h3) {
  font-weight: bold;
}

:where(p, li) {
  color: purple;
}

a:has(img) {
  text-decoration: underline;
}
```

## Pseudo-classes de Formulário

### `:disabled`

- Seleciona elementos de formulário desabilitados.

```css
input:disabled {
    background-color: #ccc;
}
```

### `:checked`

- Seleciona elementos de formulário que estão marcados (checkboxes ou radios).

```css
input[type="radio"]:checked {
    border-color: green;
}
```

### `:required` e `:optional`

A pseudo-classe `:required` seleciona elementos de entrada que são obrigatórios, enquanto `:optional` seleciona elementos de entrada que são opcionais.

```css
input:required {
  border: 2px solid red;
}

input:optional {
  border: 2px solid gray;
}
```

## Pseudo-elementos

### `::before` e `::after`

- Os pseudo-elementos `::before` e `::after` permitem inserir conteúdo antes ou depois do conteúdo real de um elemento HTML.

```css
p::before {
  content: "Antes: ";
}

p::after {
  content: " Depois.";
}
```

### `::first-letter` e `::first-line`

- `::first-letter` seleciona a primeira letra dentro de um elemento e `::first-line` seleciona a primeira linha de texto.

```css
p::first-letter {
  font-size: 150%;
}

p::first-line {
  font-weight: bold;
}
```

### `::selection`

- `::selection` permite estilizar o texto selecionado pelo usuário em uma página.

```css
::selection {
  background-color: yellow;
  color: black;
}
```