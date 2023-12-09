# Importação no Sass

## Importando Arquivos no Sass

O Sass mantém o código CSS DRY (Don't Repeat Yourself). Uma maneira de escrever código DRY é manter código relacionado em arquivos separados.

Você pode criar pequenos arquivos com trechos de CSS para incluir em outros arquivos Sass. Exemplos de tais arquivos podem ser: arquivo de reset, variáveis, cores, fontes, tamanhos de fonte, etc.

### Importando Arquivos no Sass

Assim como o CSS, o Sass também suporta a diretiva @import.

A diretiva @import permite incluir o conteúdo de um arquivo em outro.

A diretiva @import do CSS tem uma grande desvantagem devido a problemas de desempenho; ela cria uma solicitação HTTP extra cada vez que é chamada. No entanto, a diretiva @import do Sass inclui o arquivo no CSS; portanto, não é necessário um chamada HTTP extra em tempo de execução!

### Sintaxe de Importação no Sass:

```scss
@import nome-do-arquivo;
```

Dica: Você não precisa especificar uma extensão de arquivo, o Sass automaticamente assume que você está se referindo a um arquivo .sass ou .scss. Você também pode importar arquivos CSS. A diretiva @import importa o arquivo e quaisquer variáveis ou mixins definidos no arquivo importado podem ser usados no arquivo principal.

Você pode importar quantos arquivos precisar no arquivo principal:

```scss
@import "variaveis";
@import "cores";
@import "reset";
```

Vamos analisar um exemplo: Suponha que temos um arquivo de reset chamado "reset.scss", que se parece com isso:

```scss
html,
body,
ul,
ol {
  margin: 0;
  padding: 0;
}
```

E agora queremos importar o arquivo "reset.scss" para outro arquivo chamado "padrao.scss".

Veja como fazemos isso: É normal adicionar a diretiva @import no topo de um arquivo; dessa forma, seu conteúdo terá um escopo global:

```scss
@import "reset";

body {
  font-family: Helvetica, sans-serif;
  font-size: 18px;
  color: red;
}
```

Então, quando o arquivo "padrao.css" é transpilado, o CSS será assim:

```css
html, body, ul, ol {
  margin: 0;
  padding: 0;
}

body {
  font-family: Helvetica, sans-serif;
  font-size: 18px;
  color: red;
}
```

## Partials no Sass

Por padrão, o Sass transpila todos os arquivos .scss diretamente. No entanto, quando você deseja importar um arquivo, você não precisa que o arquivo seja transpilado diretamente.

O Sass tem um mecanismo para isso: Se você começar o nome do arquivo com um sublinhado, o Sass não o transpilará. Arquivos nomeados dessa maneira são chamados de partials no Sass.

Então, um arquivo Sass partial é nomeado com um sublinhado no início:

### Sintaxe de Partial Sass:

O exemplo a seguir mostra um arquivo Sass partial chamado `_cores.scss`. (Este arquivo não será transpilado diretamente para "cores.css"):

### Exemplo

```scss
$meuRosa: #EE82EE;
$meuAzul: #4169E1;
$meuVerde: #8FBC8F;
```

Agora, se você importar o arquivo parcial, omita o sublinhado. O Sass entende que deve importar o arquivo "_cores.scss":

### Exemplo

```scss
@import "cores";

body {
  font-family: Helvetica, sans-serif;
  font-size: 18px;
  color: $meuAzul;
}
```