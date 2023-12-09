# Aninhamento o no Sass

## Regras Aninhadas no Sass

O Sass permite aninhar seletores CSS da mesma forma que no HTML.

Considere um exemplo de código Sass para a navegação de um site:

### Exemplo

```scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  li {
    display: inline-block;
  }
  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

Observe que no Sass, os seletores ul, li e a estão aninhados dentro do seletor nav.

Enquanto no CSS, as regras são definidas uma por uma (não aninhadas):

### CSS Correspondente

```css
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

Por permitir o aninhamento de propriedades no Sass, o código torna-se mais limpo e fácil de ler em comparação com o CSS padrão.

## Propriedades Aninhadas no Sass

Muitas propriedades CSS compartilham o mesmo prefixo, como font-family, font-size e font-weight, ou text-align, text-transform e text-overflow.

Com Sass, você pode escrevê-las como propriedades aninhadas:

### Exemplo

```scss
font: {
  family: Helvetica, sans-serif;
  size: 18px;
  weight: bold;
}

text: {
  align: center;
  transform: lowercase;
  overflow: hidden;
}
```

O transpilador Sass converterá o acima para CSS normal:

### Saída CSS

```css
font-family: Helvetica, sans-serif;
font-size: 18px;
font-weight: bold;

text-align: center;
text-transform: lowercase;
text-overflow: hidden;
```

Ao utilizar regras e propriedades aninhadas no Sass, você pode organizar seu código de maneira mais intuitiva, tornando-o mais fácil de entender e manter.