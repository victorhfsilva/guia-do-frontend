# Mixins no Sass

A diretiva @mixin permite criar código CSS que pode ser reutilizado em todo o site.

A diretiva @include é criada para permitir o uso (inclusão) do mixin.

## Definindo um Mixin

Um mixin é definido com a diretiva @mixin.

## Sintaxe do Mixin no Sass:

```scss
@mixin nome {
  propriedade: valor;
  propriedade: valor;
  // ...
}
```

O exemplo a seguir cria um mixin chamado "important-text":

```scss
@mixin important-text {
  color: red;
  font-size: 25px;
  font-weight: bold;
  border: 1px solid blue;
}
```

Dica: Hífens e underscores são considerados iguais no Sass. Isso significa que @mixin important-text { } e @mixin important_text { } são considerados o mesmo mixin!

## Utilizando um Mixin

A diretiva @include é usada para incluir um mixin.

### Sintaxe de Inclusão de Mixin no Sass:

```scss
seletor {
  @include nome-do-mixin;
}
```

Portanto, para incluir o mixin "important-text" criado acima:


```scss
.danger {
  @include important-text;
  background-color: green;
}
```

### Saída CSS

O transpilador Sass, por sua vez, converterá a estilização acima para CSS normal:


```css
.danger {
  color: red;
  font-size: 25px;
  font-weight: bold;
  border: 1px solid blue;
  background-color: green;
}
```
## Mixins aninhados

Um mixin também pode incluir outros mixins:

```scss
@mixin special-text {
  @include important-text;
  @include link;
  @include special-border;
}
```

## Passando Variáveis para um Mixin

Mixins aceitam argumentos. Dessa forma, você pode passar variáveis para um mixin.

Aqui está como definir um mixin com argumentos:

```scss
/* Define mixin com dois argumentos */
@mixin bordered($cor, $largura) {
  border: $largura solid $cor;
}

.myArticle {
  @include bordered(azul, 1px); // Chama o mixin com dois valores
}

.myNotes {
  @include bordered(vermelho, 2px); // Chama o mixin com dois valores
```

Observe que os argumentos são definidos como variáveis e depois usados como os valores (cor e largura) da propriedade border.

Após a compilação, o CSS será semelhante a isto:

### Saída CSS

```css
.myArticle {
  border: 1px solid blue;
}

.myNotes {
  border: 2px solid red;
}
```

### Valores Padrão para um Mixin

Também é possível definir valores padrão para variáveis de mixin:

```scss
@mixin bordered($cor: azul, $largura: 1px) {
  border: $largura solid $cor;
}
```

Então, você só precisa especificar os valores que mudam ao incluir o mixin:


```scss
.myTips {
  @include bordered($cor: laranja);
}
```

Ao usar mixins no Sass, você pode criar e reutilizar blocos de código de maneira eficiente, facilitando a manutenção e a organização do seu código CSS.