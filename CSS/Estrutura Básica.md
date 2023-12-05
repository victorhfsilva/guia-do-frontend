# Estrutura Básica do CSS

O CSS (Cascading Style Sheets) é uma linguagem de estilo usada para controlar a aparência e o layout de elementos HTML em uma página da web. 

## Estrutura Básica de um Arquivo CSS

Um arquivo CSS é composto por regras de estilo que especificam como os elementos HTML devem ser exibidos. A estrutura básica de um arquivo CSS é a seguinte:

```css
seletor {
    propriedade: valor;
    /* Mais propriedades e valores */
}
```

- `seletor`: Define o elemento HTML que será estilizado.
- `propriedade`: Define a característica que será estilizada (por exemplo, `color`, `font-size`, `background-color`).
- `valor`: Especifica o valor da propriedade (por exemplo, `red`, `16px`, `#FFFFFF`).

### Estilizando um Elemento HTML

- Neste exemplo, o seletor `h1` seleciona todos os cabeçalhos de nível 1 (`<h1>`) e define a cor do texto como azul e o tamanho da fonte como 24 pixels.

```css
h1 {
    color: blue;
    font-size: 24px;
}
```

## Seletores
### Seletores de Classes e IDs

```css
.botao {
    background-color: #007bff;
    color: #fff;
    padding: 10px 20px;
}

#destaque {
    font-weight: bold;
    text-decoration: underline;
}
```

- `.botao` seleciona elementos com a classe `botao`.
- `#destaque` seleciona um elemento com o ID `destaque`.

### Combinando Seletor de Classes e Elementos

- Neste exemplo, `p.destaque` seleciona parágrafos (`<p>`) com a classe `destaque` e define o fundo como amarelo e a fonte em negrito.

```css
p.destaque {
    background-color: yellow;
    font-weight: bold;
}
```

### Seletores Globais

- O exemplo a seguir define a fonte de todos os elementos como negritas.

```css
* {
    font-weight: bold;
}
```

### Seletores de Atributos

- O exemplo a seguir define todos os elementos que contenham o atributo title como sendo vermelhos.

```css
[title] {
    color: red;
}
```

- O exemplo a seguir define todos os elementos que contenham o atributo title como sendo Titulo com a cor verde. 

```css
[title = "Titulo"] {
    color: green;
}
```

- O exemplo a seguir define todos os elementos que contenham a palavra Word no atributo title como sendo brancos.

```css
[title ~= "Word"] {
    color: white;
}
```

- O exemplo a seguir estiliza apenas os elementos cujo atributo href possuam prefixo http:// . 

```css
[href ^= "http://"] {
    color: red;
}
```

- O exemplo a seguir estiliza apenas os elementos cujo atributo href possua um sufixo login.

```css
[href $= "login"] {
    color: green;
}
```

- O exemplo a seguir estiliza todos os elementos cujo atributo href possua a string login, independente da posição.


```css
[href *= "login"] {
    color: green;
}
```


## Combinadores

### Agrupamento de seletores

Para agrupar diferentes seletores basta separa-los por virgulas.

```css
h2, .title, [id $= title] {
    font-weight: bold;
}
```

Caso qualquer um dos seletores seja satisfeito a estilização será performada. Ou seja, o agrupamento por vírgula funciona como uma operação ou.

### Combinador descendente

```css
#lista li {
    color: black;
}
```

Esta combinação irá estilizar todos os elementos de lista li, presentes na lista de id lista. Ou seja, irá estilizar todos os subitens da lista de id lista.

### Combinador Filho 

```css
#lista > li {
    color: pink;
}
```

Esta combinação apenas irá estilizar os elementos filhos de #lista. Os elementos netos, ou seja os elementos que são filhos dos seus filhos, não serão estilizados.

### Combinador Irmão Adjacente

```css
#login-input + input {
    background: transparent;
}
```

Esta combinação irá estilizar o primeiro elemento do tipo input após #login-input, o seu irmão adjacente.

### Combinador Irmão Geral

```css
input ~ p {
    font-sytle: italic;
}
```

Esta combinação irá estilizar todos os elementos do tipo p que estiverem próximos de um input.

## Comentários em CSS

Os comentários são úteis para documentar seu código CSS:

```css
/* Este é um comentário em CSS. */
```

## Vinculando um Arquivo CSS a um Documento HTML

### Vínculo externo

Para aplicar um arquivo CSS a um documento HTML, você pode usar a tag `<link>` no `<head>` do HTML:

```html
<!DOCTYPE html>
<html>
    <head>
        <link rel="stylesheet" type="text/css" href="styles.css">
    </head>
    <body>
        <!-- Conteúdo HTML -->
    </body>
</html>
```

Certifique-se de substituir `"styles.css"` pelo caminho real do seu arquivo CSS.

## Vínculo Interno

Você também pode incluir CSS diretamente no `<head>` do documento HTML usando a tag `<style>`:

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        h1 {
            color: green;
        }
    </style>
</head>
<body>
    <!-- Conteúdo HTML -->
</body>
</html>
```

## Declaração Inline

```html
<h1 style="color: green; font-size: 24px;">
    Título
</h1>
```