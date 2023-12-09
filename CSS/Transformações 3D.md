# Transformações 3D em CSS

As transformações 3D em CSS permitem modificar a posição, rotação, escala e perspectiva de elementos em um espaço tridimensional. Aqui está um guia para as principais transformações 3D e suas propriedades relacionadas:

### Transformações Básicas

#### `translate3d(x, y, z)`

- A função `translate3d(x, y, z)` move um elemento nas direções horizontal (x), vertical (y) e no eixo Z.

```css
.element {
  transform: translate3d(20px, 30px, 10px); /* Move 20px para a direita, 30px para baixo e 10px no eixo Z */
}
```

#### `rotateX(angle)`, `rotateY(angle)` e `rotateZ(angle)`

- As funções `rotateX(angle)`, `rotateY(angle)` e `rotateZ(angle)` realizam rotações em torno dos eixos X, Y e Z, respectivamente.

```css
.element {
  transform: rotateX(45deg); /* Rotação de 45 graus em torno do eixo X */
}
```

#### `scale3d(x, y, z)`

- A função `scale3d(x, y, z)` aumenta ou diminui o tamanho de um elemento nas direções horizontal (x), vertical (y) e no eixo Z.

```css
.element {
  transform: scale3d(1.5, 0.5, 2); /* Aumenta em 150% na horizontal, diminui em 50% na vertical e aumenta em 200% no eixo Z */
}
```

### Propriedades Relacionadas

#### `transform-origin`

- A propriedade `transform-origin` define o ponto de origem das transformações. Ele permite que você especifique o centro de rotação e escala.

```css
.element {
  transform-origin: center center;
}
```

#### `transform-style`

- A propriedade `transform-style` define como elementos filhos são renderizados em um contexto 3D. O valor `preserve-3d` mantém a estrutura tridimensional.

```css
.container {
  transform-style: preserve-3d;
}
```

### Perspectiva

#### `perspective`

- A propriedade `perspective` define a perspectiva da cena tridimensional. Ela afeta a profundidade das transformações 3D.

```css
.container {
  perspective: 1000px; /* Define a perspectiva de 1000 pixels */
}
```

### Visibilidade das Faces de Trás

#### `backface-visibility`

- A propriedade `backface-visibility` controla a visibilidade das faces de trás dos elementos durante rotações.

```css
.element {
  backface-visibility: hidden; /* Oculta as faces de trás durante rotações */
}
```

### Função `matrix3d()`

- A função `matrix3d()` permite aplicar uma matriz de transformação 3D personalizada para combinar várias transformações em um único elemento.

```css
.element {
  transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 20, 30, 10, 1);
}
```

## Conclusão

As transformações 3D em CSS oferecem a capacidade de criar efeitos visuais tridimensionais e interativos em elementos HTML. Com a combinação adequada de propriedades e funções de transformação, você pode projetar experiências de usuário mais envolventes em suas páginas da web.