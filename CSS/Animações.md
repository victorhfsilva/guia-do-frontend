## Animações em CSS

As animações em CSS permitem criar efeitos de transição suaves e interativos em elementos HTML. Aqui está um guia completo para animações, incluindo conceitos importantes e exemplos:

### Transições Básicas

#### `transition-property`

- Define as propriedades CSS a serem animadas.

```css
.element {
  transition-property: width, height, color;
}
```

#### `transition-duration`

- Define a duração da animação.

```css
.element {
  transition-duration: 1s; /* Duração de 1 segundo */
}
```

#### `transition-timing-function`

- Define a curva de velocidade da animação (por exemplo, linear, ease-in, ease-out, ease-in-out).

```css
.element {
  transition-timing-function: ease-in-out;
}
```

#### `transition-delay`

- Define um atraso antes de iniciar a animação.

```css
.element {
  transition-delay: 0.5s; /* Atraso de 0,5 segundos */
}
```

### Exemplo de Transição

Aqui está um exemplo de como usar transições para suavizar mudanças de cor em um botão quando o mouse passa por cima dele:

```css
.button {
  background-color: #3498db;
  color: #fff;
  transition-property: background-color, color;
  transition-duration: 0.3s;
  transition-timing-function: ease-in-out;
}

.button:hover {
  background-color: #e74c3c;
  color: #fff;
}
```

### Animações Personalizadas

#### `@keyframes`

- Define uma animação personalizada usando a regra `@keyframes`. Ela especifica os estados iniciais e finais da animação.

```css
@keyframes example {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  100% {
    transform: scale(1.2);
    opacity: 0;
  }
}
```

#### `animation-name`

- Define o nome da animação personalizada definida com `@keyframes`.

```css
.element {
  animation-name: example;
}
```

#### `animation-duration`

- Define a duração da animação personalizada.

```css
.element {
  animation-duration: 2s; /* Duração de 2 segundos */
}
```

#### `animation-timing-function`

- Define a curva de velocidade da animação personalizada.

```css
.element {
  animation-timing-function: cubic-bezier(0.25, 0.1, 0.25, 1);
}
```

#### `animation-delay`

- Define um atraso antes de iniciar a animação personalizada.

```css
.element {
  animation-delay: 1s; /* Atraso de 1 segundo */
}
```

#### `animation-iteration-count`

- Define o número de vezes que a animação deve ser reproduzida.

```css
.element {
  animation-iteration-count: infinite; /* Reprodução infinita */
}
```

#### `animation-direction`

- Define a direção da reprodução da animação (normal, reverse, alternate, alternate-reverse).

```css
.element {
  animation-direction: alternate; /* Direção alternada */
}
```

#### `animation-fill-mode`

- Define como as propriedades animadas devem ser aplicadas antes e depois da animação (none, forwards, backwards, both).

```css
.element {
  animation-fill-mode: forwards; /* Aplicar propriedades após a animação */
}
```

### Shorthand `animation`

- A propriedade `animation` combina todas as propriedades de animação em uma única linha.

```css
.element {
  animation: example 2s ease-in-out 1s infinite alternate forwards;
}
```

### Pausando Animações

#### `animation-play-state`

- Define se a animação está pausada ou em execução.

```css
.element {
  animation-play-state: paused; /* Pausa a animação */
}
```

### Exemplo de Animação Personalizada

Aqui está um exemplo de como criar uma animação personalizada que faz um elemento se mover de um canto ao outro e girar:

```css
@keyframes moveAndRotate {
  0% {
    transform: translateX(0) rotate(0deg);
  }
  50% {
    transform: translateX(200px) rotate(180deg);
  }
  100% {
    transform: translateX(0) rotate(360deg);
  }
}

.element {
  animation: moveAndRotate 3s ease-in-out 1s infinite alternate both;
}
```

## Conclusão

As animações em CSS são ferramentas poderosas para criar transições suaves e efeitos personalizados em elementos HTML. Com o uso adequado das propriedades e regras de animação, você pode tornar suas páginas da web mais atraentes e interativas.