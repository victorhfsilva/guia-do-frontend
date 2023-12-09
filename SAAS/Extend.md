# @extend no Sass

## Diretiva @extend no Sass

A diretiva @extend permite compartilhar um conjunto de propriedades CSS de um seletor para outro.

A diretiva @extend é útil se você tiver elementos estilizados de forma quase idêntica que diferem apenas em alguns detalhes pequenos.

O exemplo Sass a seguir primeiro cria um estilo básico para botões (este estilo será usado para a maioria dos botões). Em seguida, criamos um estilo para um botão "Report" e um estilo para um botão "Submit". Ambos os botões "Report" e "Submit" herdam todas as propriedades CSS da classe .button-basic por meio da diretiva @extend. Além disso, eles têm suas próprias cores definidas:

### Sintaxe SCSS:

```scss
.button-basic {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}

.button-report {
  @extend .button-basic;
  background-color: red;
}

.button-submit {
  @extend .button-basic;
  background-color: green;
  color: white;
}
```

Após a compilação, o CSS será assim:

### Saída CSS:

```css
.button-basic, .button-report, .button-submit {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}

.button-report {
  background-color: red;
}

.button-submit {
  background-color: green;
  color: white;
}
```

Ao usar a diretiva @extend, você não precisa especificar várias classes para um elemento em seu código HTML, como este: `<button class="button-basic button-report">Reportar isso</button>`. Basta especificar ``.button-report`` para obter ambos os conjuntos de estilos.

A diretiva @extend ajuda a manter seu código Sass muito DRY (Don't Repeat Yourself).