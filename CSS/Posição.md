# Propriedade `position` em CSS

A propriedade `position` em CSS é usada para controlar o posicionamento de elementos em uma página da web. Ela permite que você especifique como um elemento deve ser posicionado em relação ao seu contexto de layout. 

## Valores da Propriedade `position`

### `static`

- Valor padrão.
- O elemento é posicionado na ordem em que ele renderizado no documento.
- Ignora as propriedades `top`, `right`, `bottom` e `left`.

```css
element {
    position: static;
}
```

### `relative`

- O elemento é posicionado relativo a sua posição normal.
- As propriedades `top`, `right`, `bottom` e `left` podem ser usadas para ajustar a posição do elemento.

```css
element {
    position: relative;
    top: 10px;
    left: 20px;
}
```

### `fixed`

- O elemento é removido do layout do container.
- E é posicionado em relação à janela de visualização (viewport).
- Mantém sua posição fixa mesmo quando a página é rolada.
- Útil para elementos como barras de navegação fixas.

```css
element {
    position: fixed;
    top: 10px;
    right: 20px;
}
```

### `sticky`

- O elemento é inicialmente posicionado como `relative`.
- Quando a posição de rolagem atinge a posição especificada, ele se comporta como `fixed`.
- Útil para criar cabeçalhos que permanecem no topo enquanto o usuário rola a página.

```css
element {
    position: sticky;
    top: 0;
}
```

Neste caso, ele se comporta como fixed quando atinge um top de 0px.

## `z-index`

- A propriedade z-index define quais elementos sobreporão os demais.
- Por padrão todos os elementos têm z-index 0.
- Os elementos de maior z-index aparecem em cima dos de menor.


## Considerações Finais

A propriedade `position` desempenha um papel crucial no controle do layout e posicionamento de elementos em uma página da web. É importante compreender como cada valor afeta o comportamento dos elementos e quando usar cada um deles. 