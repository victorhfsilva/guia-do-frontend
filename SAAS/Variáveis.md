# Variáveis no Sass

## Introdução às Variáveis no Sass

As variáveis no Sass oferecem uma maneira de armazenar informações que podem ser reutilizadas posteriormente em seu código. Elas podem representar strings, números, cores, booleanos, listas e nulos.

### Sintaxe de Variáveis no Sass:

```scss
$nomevariavel: valor;
```

Exemplo:

```scss
$minhaFonte: Helvetica, sans-serif;
$minhaCor: vermelho;
$minhaTamanhoFonte: 18px;
$minhaLargura: 680px;
```

### Utilizando Variáveis:

```scss
body {
  font-family: $minhaFonte;
  font-size: $minhaTamanhoFonte;
  color: $minhaCor;
}

#container {
  width: $minhaLargura;
}
```

### Saída CSS:

```css
body {
  font-family: Helvetica, sans-serif;
  font-size: 18px;
  color: red;
}

#container {
  width: 680px;
}
```

## Escopo de Variáveis no Sass

As variáveis no Sass têm um escopo limitado à aninhamento onde são definidas. Considere o exemplo a seguir:

```scss
$minhaCor: red;

h1 {
  $minhaCor: green;
  color: $minhaCor;
}

p {
  color: $minhaCor;
}
```

A cor do texto dentro de uma tag `<p>` será vermelha, pois a definição `$minhaCor: green;` está dentro da regra `<h1>` e só é válida lá. O escopo padrão é limitado.

### Usando `!global` no Sass

Para tornar uma variável global, ou seja, acessível em todos os níveis, podemos usar `!global`. Veja o exemplo ajustado:

```scss
$minhaCor: red;

h1 {
  $minhaCor: green !global;
  color: $minhaCor;
}

p {
  color: $minhaCor;
}
```

Agora, a cor do texto dentro de uma tag `<p>` será verde, pois `$minhaCor: green !global;` torna a variável global.

### Dica: Definindo Variáveis Globais

Para evitar problemas, é aconselhável definir variáveis globais fora de regras específicas. Pode ser sábio agrupar todas as variáveis globais em um arquivo separado, chamado "_globals.scss", e incluir o arquivo usando `@include`.