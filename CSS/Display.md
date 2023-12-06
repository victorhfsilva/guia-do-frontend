# Propriedade `display` em CSS

A propriedade `display` é usada em CSS para controlar como um elemento HTML é exibido na página. Ela determina o modelo de renderização do elemento, afetando sua aparência e comportamento. 

## Valores da Propriedade `display`

### 1. `block`

- O elemento é exibido como um bloco, ocupando toda a largura disponível.
- O elemento inicia em uma nova linha, empurrando os elementos subsequentes para baixo.
- Exemplos: `<div>`, `<p>`, `<h1>`, `<form>`.

```css
div {
    display: block;
}
```

### 2. `inline`

- O elemento é exibido em linha, ocupando apenas o espaço necessário para seu conteúdo.
- Os elementos subsequentes fluem na mesma linha.
- Exemplos: `<span>`, `<a>`, `<strong>`, `<em>`, `<b>``.

```css
span {
    display: inline;
}
```

- Para alinhar elementos de containers inline ou inline-block horizontalmente pode-se utilizar o `text-align`, mesmo que os componentes não sejam textos.
- Já para alinhar estes elementos verticalmente basta utilizar o `vertical-align`.

### 3. `inline-block`

- O elemento é exibido em linha, mas permite a definição de largura e altura, como um bloco.
- Elementos subsequentes fluem na mesma linha.
- Combina características de elementos `inline` e `block`.
- Útil para criar layouts de linha com elementos de bloco.
- Exemplos: Botões, caixas de seleção.

```css
button {
    display: inline-block;
    width: 240px;
    height: 80px;
    margin: 10px;
    padding: 20px;
}
```

### 4. `none`

- O elemento não é renderizado na página e fica oculto.
- É como se o elemento não existisse na estrutura do documento.
- Pode ser usado para ocultar elementos de forma dinâmica com JavaScript.

```css
.hidden-element {
    display: none;
}
```

- Também é possível alcançar um resultado similar utilizando o `visibility: hidden`. Porém, com esta alternativa mantêm o espaço deste elemento.

### 5. `flex`

- Introduz um modelo de layout flexível.
- Os elementos filhos se comportam como itens flexíveis dentro de um container flex.
- Permite a distribuição do espaço disponível entre os itens flexíveis.
- Útil para criar layouts complexos e responsivos.
- Exemplos: Container de navegação, grades flexíveis.

```css
.container {
    display: flex;
}
```

### 6. `grid`

- Introduz um modelo de layout de grade bidimensional.
- Os elementos filhos se tornam células em uma grade.
- Oferece controle preciso sobre a posição e o tamanho dos elementos.
- Útil para criar layouts complexos em grade.
- Exemplos: Layouts de página, galerias de imagens.

```css
.grid-container {
    display: grid;
}
```

### 7. `inherit` e `initial`

- `inherit`: O elemento herda a propriedade `display` de seu elemento pai.
- `initial`: Define a propriedade `display` como seu valor inicial.

```css
.child {
    display: inherit; /* Herda o valor de display do elemento pai */
}

.reset {
    display: initial; /* Define display como seu valor inicial */
}
```

### 8. Outros Valores Possíveis

Além dos valores mencionados anteriormente, a propriedade `display` em CSS possui outros valores que podem ser utilizados em casos específicos. Alguns desses valores incluem:

- `table`: O elemento se comporta como um elemento de tabela.
- `table-cell`: O elemento se comporta como uma célula de tabela.
- `table-row`: O elemento se comporta como uma linha de tabela.
- `flex-inline`: Similar ao `flex`, mas os elementos são tratados como `inline`.
- `inline-table`: O elemento se comporta como uma tabela em linha.
- `list-item`: O elemento se comporta como um item de lista.
- `run-in`: O elemento é renderizado como blocos ou em linha, dependendo do contexto.

Estes valores adicionais proporcionam flexibilidade para adaptar a exibição de elementos de acordo com as necessidades específicas do layout e design da página. Para mais informações consulte [CSS display Property](https://www.w3schools.com/cssref/pr_class_display.php).