# Tabelas em HTML

As tabelas em HTML permitem organizar e exibir dados de maneira tabular. Elas são compostas por várias tags que definem a estrutura da tabela, como linhas, colunas e células.

## Estrutura Básica de uma Tabela

```html
<table>
    <caption>Título da Tabela</caption>
    <thead>
        <tr>
            <th>Cabeçalho 1</th>
            <th>Cabeçalho 2</th>
            <th>Cabeçalho 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Dado 1</td>
            <td>Dado 2</td>
            <td>Dado 3</td>
        </tr>
        <tr>
            <td>Dado 4</td>
            <td>Dado 5</td>
            <td>Dado 6</td>
        </tr>
    </tbody>
</table>
```

### Componentes de uma Tabela

- `<table>`: Define a tabela.
- `<caption>`: Opcional. Define um título para a tabela.
- `<thead>`: O cabeçalho da tabela.
- `<tr>`: Define uma linha na tabela.
- `<th>`: Define uma célula de cabeçalho.
- `<tbody>`: O corpo da tabela.
- `<td>`: Define uma célula de dados.

## Atributos de Tabela

### `border`

Define a largura da borda da tabela. Geralmente, 0 para tabelas sem bordas e 1 para tabelas com bordas.

```html
<table border="1">
```

### `width`

Define a largura da tabela em pixels ou porcentagem.

```html
<table width="100%">
```

## Combinando Células

Você pode combinar células horizontal ou verticalmente usando os atributos `colspan` e `rowspan`.

```html
<td colspan="2">Célula combinada horizontalmente</td>
<td rowspan="3">Célula combinada verticalmente</td>
```

## Estilos CSS

Use CSS para aplicar estilos à sua tabela, como cores de fundo, bordas e tamanhos de fonte.

```css
table {
    border-collapse: collapse; /* Combina bordas de células adjacentes */
    width: 100%;
}

th, td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
}

th {
    background-color: #f2f2f2;
}
```

## Tabelas Responsivas

Para tornar tabelas responsivas em dispositivos móveis, você pode usar a propriedade CSS `overflow-x` e adicionar uma barra de rolagem horizontal quando a tela estiver muito estreita para a tabela.

```css
table {
    overflow-x: auto;
}
```

As tabelas são uma maneira eficaz de exibir e organizar dados em uma página da web. Certifique-se de usar as tags e atributos apropriados para criar tabelas acessíveis e bem estruturadas. Use CSS para personalizar o estilo da tabela de acordo com suas necessidades.