# Listas em HTML

As listas são elementos fundamentais em HTML usados para organizar informações de forma estruturada. Existem três tipos principais de listas em HTML: listas ordenadas, listas não ordenadas e listas por definição.

## Listas Ordenadas (`<ol>`)

As listas ordenadas são usadas quando a ordem dos itens é importante. Os itens são numerados por padrão, mas a numeração pode ser personalizada.

```html
<ol>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ol>
```

### Atributos `<ol>`

- `type`: Define o tipo de marcador (1, A, a, I, i).
- `start`: Define o valor inicial da contagem.

## Listas Não Ordenadas (`<ul>`)

As listas não ordenadas são usadas quando a ordem dos itens não é importante. Os itens são geralmente marcados com um ponto, mas o marcador pode ser personalizado.

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

### Atributos `<ul>`

- `type`: Define o tipo de marcador (disc, circle, square).

## Listas por Definição (`<dl>`)

As listas por definição são usadas para definir termos e suas respectivas definições. Elas consistem em pares de termos (`<dt>`) e definições (`<dd>`).

```html
<dl>
    <dt>Termo 1</dt>
    <dd>Definição 1</dd>
    <dt>Termo 2</dt>
    <dd>Definição 2</dd>
</dl>
```

### Atributos `<dt>` e `<dd>`

- `<dt>` não possui atributos especiais.
- `<dd>` é usado para definir a definição do termo.

## Listas Aninhadas

Você pode criar listas aninhadas, colocando uma lista dentro de outra. Isso é útil para criar subitens.

```html
<ul>
    <li>Item 1</li>
    <li>Item 2
        <ul>
            <li>Subitem 1</li>
            <li>Subitem 2</li>
        </ul>
    </li>
    <li>Item 3</li>
</ul>
```

## Listas Personalizadas

Você pode personalizar a aparência de listas não ordenadas e ordenadas usando CSS. Por exemplo, para criar uma lista de verificação:

```html
<ul class="checklist">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

```css
.checklist {
    list-style-type: square;
}
```

As listas são uma maneira eficaz de organizar informações em seu site ou documento HTML. Escolha o tipo de lista apropriado com base na natureza dos dados que você deseja apresentar e use CSS para personalizar a aparência, quando necessário.
