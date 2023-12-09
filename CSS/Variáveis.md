# Variáveis em CSS

As variáveis em CSS, também conhecidas como variáveis personalizadas, oferecem uma maneira eficaz de reutilizar valores em propriedades CSS. Elas tornam o código mais legível, manutenível e permitem a criação de estilos mais flexíveis e dinâmicos. Abaixo, você encontrará um guia de referência rápida sobre o uso de variáveis em CSS.

## Declaração de Variáveis

### Definir uma variável:

```css
--nome-da-variavel: valor;
```

Exemplo:

```css
--cor-destaque: #ff5733;
```

## Uso de Variáveis

### Acessar uma variável:

```css
propriedade: var(--nome-da-variavel);
```

Exemplo:

```css
background-color: var(--cor-destaque);
```

## Escopo de Variáveis

As variáveis em CSS podem ser definidas em diferentes escopos:

### Escopo Global:

Variáveis definidas no `:root` têm escopo global.

```css
:root {
  --cor-destaque: #ff5733;
}
```

### Escopo Local:

Variáveis definidas dentro de seletores têm escopo local.

```css
.button {
  --tamanho-fonte: 16px;
}
```

## Valores Padrão

É possível fornecer um valor padrão para variáveis em caso de não definição.

```css
propriedade: var(--nome-da-variavel, valor-padrao);
```

Exemplo:

```css
font-size: var(--tamanho-fonte, 14px);
```

## Alterando Variáveis com JavaScript

Variáveis CSS podem ser alteradas dinamicamente usando JavaScript.

```javascript
document.documentElement.style.setProperty('--nome-da-variavel', 'novo-valor');
```

## Vantagens de Variáveis em CSS

- **Reutilização:** Evita repetição de valores em propriedades CSS.
- **Manutenção:** Facilita a atualização de estilos em todo o site.
- **Flexibilidade:** Permite estilos dinâmicos e temáticos.
- **Legibilidade:** Torna o código mais claro e organizado.

## Exemplo Completo

```css
:root {
  --cor-destaque: #ff5733;
  --tamanho-fonte: 16px;
}

.button {
  background-color: var(--cor-destaque);
  font-size: var(--tamanho-fonte);
}
```

As variáveis em CSS são uma ferramenta poderosa para criar estilos flexíveis e de fácil manutenção. Elas melhoram a coesão e a reutilização de estilos em projetos, tornando o desenvolvimento web mais eficiente.