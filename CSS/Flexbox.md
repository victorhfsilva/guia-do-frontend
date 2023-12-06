# Flexbox em CSS

O Flexbox (Flexible Box Layout) é um modelo de layout que permite criar designs complexos e alinhados facilmente em um único eixo ou em ambos. Ele é especialmente útil para criar layouts responsivos e distribuir espaço de maneira eficiente. 

## Estrutura Básica

Para usar o Flexbox, primeiro crie um container flexível que contém um ou mais elementos filho que se tornarão itens flexíveis.

```css
.container {
    display: flex; /* Torna o container um flex container */
}
```

## Propriedades do Container

### Display
#### `display: flex;`

- Define um container como um flex container.
- Os elementos filhos se tornam itens flexíveis.
- Cada flex container ocupa sua própria linha.

#### `display: inline-flex;`

- Sua única diferença com o flex é que permite que flex containers ocupem a mesma linha.

#### `flex-direction: row;`

- Define o eixo principal como horizontal (da esquerda para a direita).

#### `flex-direction: row-reverse;`

- Define o eixo principal como o horizontal porém da direita para esquerda.

#### `flex-direction: column;`

- Define o eixo principal como vertical (de cima para baixo).

#### `flex-direction: column-reverse;`

- Define o eixo principal como o vertical porém de baixo para cima.

### Quebra de Linha

#### `flex-wrap: nowrap;`

- Impede que os itens flexíveis quebrem para um novo eixo.

#### `flex-wrap: wrap;`

- Permite que os itens flexíveis quebrem para novos eixos caso necessário.

### Flex-Flow

- Para definir tanto o `flex-direction`quanto o `flex-wrap` em uma mesma linha basta utilizar o `flex-flow`:

```css
flex-flow: row nowrap;
```

### Alinhando os elementos no eixo principal

#### `justify-content: flex-start;`

- Alinha os itens flexíveis no início do container ao longo do eixo principal.

#### `justify-content: center;`

- Alinha os itens flexíveis no centro do container ao longo do eixo principal.

#### `justify-content: flex-end;`

- Alinha os itens flexíveis no final do container ao longo do eixo principal.

#### `justify-content: space-between;`

- Distribui o espaço disponível uniformemente entre os itens flexíveis, criando espaços iguais entre eles.

#### `justify-content: space-around;`

- Similar ao space-between porém também distribui o espaço entre o primeiro e o último item.

#### `justify-content: space-evenly;`

- Similar ao space-around porém também distribui o mesmo espaço entre todos os itens, o início e o fim do container.

### Valores da Propriedade `align-content`

O `align-content` é utilizado para alinhar as linhas de flex container quando este quebra suas linhas. (`flex-wrap: wrap;`)

#### 1. `flex-start`

- Alinha as linhas de elementos flexíveis no início do container ao longo do eixo transversal.

#### 2. `center`

- Alinha as linhas de elementos flexíveis no centro do container ao longo do eixo transversal.

#### 3. `flex-end`

- Alinha as linhas de elementos flexíveis no final do container ao longo do eixo transversal.

#### 4. `space-between`

- Distribui o espaço disponível uniformemente entre as linhas de elementos flexíveis, criando espaços iguais entre elas.

#### 5. `space-around`

- Similar ao `space-between`, mas também distribui o espaço entre a primeira linha e a última linha e entre as bordas do container.

#### 6. `stretch`

- O valor padrão. Faz com que as linhas de elementos flexíveis se estendam para preencher todo o espaço disponível no eixo transversal.

### Alinhando os elementos no eixo transversal

#### `align-items: flex-start;`

- Alinha os itens flexíveis no início do container ao longo do eixo transversal.

#### `align-items: center;`

- Alinha os itens flexíveis no centro do container ao longo do eixo transversal.

#### `align-items: flex-end;`

- Alinha os itens flexíveis no final do container ao longo do eixo transversal.

#### `align-items: stretch;`

- Faz com que os itens flexíveis se estendam para preencher todo o eixo transversal.

### Valores da Propriedade `align-self`

A propriedade `align-self` aceita os seguintes valores:

- `flex-start`: Alinha o elemento no início do eixo transversal.
- `flex-end`: Alinha o elemento no final do eixo transversal.
- `center`: Alinha o elemento no centro do eixo transversal.
- `baseline`: Alinha o elemento à linha de base de outros elementos (com base no conteúdo de texto).
- `stretch` (valor padrão): O elemento se estende para ocupar todo o espaço disponível no eixo transversal.


#### Uso Prático

A propriedade `align-self` é útil em várias situações, como:

1. **Ajuste Individual**: Alinhar elementos flexíveis individualmente dentro de um container flexível sem afetar outros elementos.

2. **Correção de Alinhamento**: Corrigir alinhamentos específicos de elementos que podem ter tamanhos diferentes ou propósitos diferentes.

3. **Layouts Responsivos**: Controlar o alinhamento vertical de elementos em layouts flexíveis responsivos, garantindo uma aparência consistente em diferentes tamanhos de tela.


### Espaçamento entre Componentes

Em CSS, o espaçamento entre linhas e colunas em layouts flexíveis e de grade é controlado pelas propriedades `row-gap` (espaçamento entre linhas) e `column-gap` (espaçamento entre colunas). Essas propriedades são especialmente úteis quando se trabalha com layouts de grade (`display: grid`) e flexíveis (`display: flex`). 

#### `row-gap`

- A propriedade `row-gap` define o espaçamento vertical entre as linhas de elementos em um layout de grade (`display: grid`) ou flexível (`display: flex`).
- É especificada em unidades de medida, como pixels (`px`) ou porcentagens (`%`).

```css
.grid-container {
    display: grid;
    row-gap: 20px; /* Espaçamento de 20 pixels entre as linhas */
}

.flex-container {
    display: flex;
    flex-direction: column;
    row-gap: 10%; /* Espaçamento de 10% entre os elementos flexíveis */
}
```

#### `column-gap`

- A propriedade `column-gap` define o espaçamento horizontal entre as colunas de elementos em um layout de grade (`display: grid`) ou flexível (`display: flex`).
- Também é especificada em unidades de medida, como pixels (`px`) ou porcentagens (`%`).

```css
.flex-container {
    display: flex;
    flex-wrap: wrap;
    column-gap: 2rem; /* Espaçamento de 2 rem entre os elementos flexíveis */
}
```

#### Usando o atalho `gap`

Você pode usar a propriedade `gap` para definir tanto o espaçamento entre linhas quanto entre colunas em uma única declaração. Isso simplifica a criação de layouts com espaçamento uniforme.

```css
.grid-container {
    display: flex;
    gap: 20px 15px; /* Espaçamento de 20px entre as linhas e 15px entre as colunas */
}
```

## Propriedades dos itens
### Ordem

- A propriedade `order` aceita valores inteiros (positivos ou negativos).
- Os elementos flexíveis são exibidos na ordem em que aparecem no código HTML por padrão, mas a propriedade `order` permite modificar essa ordem de exibição.

```css
.flex-container {
    display: flex;
}

.flex-item {
    order: 1; /* Todos os elementos têm ordem 0 por padrão */
}

.flex-item:nth-child(2) {
    order: 2; /* Segundo elemento aparecerá primeiro */
}

.flex-item:nth-child(3) {
    order: -1; /* Terceiro elemento aparecerá por último */
}
```

### Flex-Grow

- A propriedade `flex-grow` aceita valores numéricos não negativos.
- Ela determina a proporção de espaço adicional que um elemento flexível deve ocupar em relação a outros elementos flexíveis dentro do mesmo container.
- Quanto maior o valor de `flex-grow`, mais espaço adicional o elemento flexível receberá em relação aos outros.

```css
.flex-container {
    display: flex;
}

.flex-item:nth-child(1) {
    flex-grow: 1; /* Pode crescer proporcionalmente em relação aos outros elementos */
}

.flex-item:nth-child(2) {
    flex-grow: 2; /* Receberá o dobro do espaço adicional do elemento 1 */
}

.flex-item:nth-child(3) {
    flex-grow: 0; /* Não crescerá, permanecerá com o tamanho original */
}
```

#### Uso Prático

A propriedade `flex-grow` é útil em várias situações, como:

1. **Distribuição Equitativa**: Distribuir espaço adicional igualmente entre elementos flexíveis para criar layouts equilibrados.

2. **Crescimento Proporcional**: Controlar como os elementos flexíveis se expandem em relação uns aos outros, permitindo que alguns elementos recebam mais espaço do que outros com base em critérios de design.

3. **Ajuste Responsivo**: Adaptar o crescimento dos elementos flexíveis em telas diferentes para otimizar a aparência e a usabilidade.


### Flex-Shrink

- A propriedade `flex-shrink` aceita valores numéricos não negativos.
- Ela determina a proporção de encolhimento de um elemento flexível em relação aos outros elementos flexíveis dentro do mesmo container quando há falta de espaço.
- Quanto maior o valor de `flex-shrink`, mais o elemento encolherá em relação aos outros.

```css
.flex-container {
    display: flex;
}

.flex-item:nth-child(1) {
    flex-shrink: 1; /* Pode encolher proporcionalmente em relação aos outros elementos */
}

.flex-item:nth-child(2) {
    flex-shrink: 2; /* Encolherá o dobro do que o elemento 1 */
}

.flex-item:nth-child(3) {
    flex-shrink: 0; /* Não encolherá, manterá o tamanho original */
}
```

#### Uso Prático

A propriedade `flex-shrink` é útil em várias situações, como:

1. **Gerenciamento de Espaço**: Controlar como os elementos flexíveis reagem quando o espaço disponível é insuficiente para acomodar todos eles. Elementos com valores mais altos de `flex-shrink` encolherão mais rapidamente.

2. **Priorização de Conteúdo**: Permitir que certos elementos encolham mais facilmente do que outros para garantir que o conteúdo mais importante seja mantido visível.

3. **Responsividade**: Adaptar o encolhimento dos elementos flexíveis em layouts responsivos para garantir que eles se ajustem a diferentes tamanhos de tela.

### Flex-Basis

- A propriedade `flex-basis` aceita valores numéricos, unidades de medida (como pixels ou porcentagens) ou palavras-chave.
- Ela define o tamanho inicial de um elemento flexível no eixo principal.
- O tamanho inicial pode ser uma largura (para um layout flexível na horizontal) ou uma altura (para um layout flexível na vertical).

```css
.flex-container {
    display: flex;
}

.flex-item {
    flex-basis: 100px; /* Tamanho inicial de 100 pixels */
}
```

### Align-Self
- A propriedade align-self é usada em layouts flexíveis (display: flex) para controlar o alinhamento vertical de um elemento flexível individualmente dentro de um container flexível.
- Ela ignora os valores definidos por `align-items`.
- Ela aceita valores que controlam o alinhamento vertical do elemento em relação ao eixo transversal, como `flex-start`, `center`, `flex-end`, `baseline` e `stretch`.

```css
.flex-container {
    display: flex;
}

.flex-item {
    align-self: flex-start; /* Alinhamento no início do eixo transversal */
}
```