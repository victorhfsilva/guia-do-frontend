# Elementos de Texto em HTML

## `<a>`

- Define um hiperlink para outras páginas ou recursos.
- Usado para criar links para diferentes partes de um documento ou sites externos.

```html
<a href="https://www.example.com">Visite o exemplo</a>
```

## `<em>`

- Define um texto enfatizado, geralmente exibido em itálico.
- Indica importância ou destaque no conteúdo.

```html
<em>Texto enfatizado</em>
```

## `<strong>`

- Define um texto fortemente enfatizado, geralmente exibido em negrito.
- Indica ênfase significativa no conteúdo.

```html
<strong>Texto enfatizado e importante</strong>
```

## `<small>`

- Define um texto com tamanho de fonte menor.
- Usado para indicar notas de rodapé, avisos legais, etc.

```html
<small>Texto menor</small>
```

## `<s>`

- Define um texto que não é mais válido ou relevante.
- Usado para riscar o texto.

```html
<s>Texto obsoleto</s>
```

## `<cite>`

- Define o título de uma obra, como um livro, filme, ou trabalho artístico.
- Ajuda a citar fontes de informações.

```html
<cite>Nome do Livro</cite>
```

## `<q>`

- Define uma citação curta dentro do texto.
- Geralmente exibido entre aspas.

```html
<p>Disse o famoso poeta <q>Escreva com o coração</q>.</p>
```

## `<dfn>`

- Define o termo ou conceito definido.
- Útil em glossários e definições.

```html
<dfn>HTML</dfn> é a linguagem de marcação de hipertexto.
```

## `<abbr>`

- Define uma abreviação ou sigla.
- Mostra a forma completa quando o cursor paira sobre o texto.

```html
<abbr title="World Wide Web">WWW</abbr>
```

## `<ruby>`, `<rt>`, `<rp>`

- `<ruby>` define uma base de texto com anotações.
- `<rt>` define a anotação de pronúncia.
- `<rp>` define o que deve ser exibido quando os navegadores não suportam anotações ruby.

```html
<ruby>
  漢 <rt>Hàn</rt>
</ruby>
```

### `<data>`

- Define um valor legível por máquinas e outro por humanos.

```html
O preço atual é <data value="50.00">R$ 50,00</data>.
```

### `<time>`

- Define uma data ou hora.
- Pode ser usado para representar datas, horas ou ambos.

```html
<time datetime="2023-10-15">15 de outubro de 2023</time>
```

### `<code>`

- Define código de programação ou texto de computador.
- Geralmente exibido em uma fonte monoespaçada.

```html
<code>function calcularImposto()</code>
```

### `<var>`

- Define uma variável em matemática ou programação.
- Indica que o texto representa uma variável.

```html
A fórmula é <var>x = 2 * y</var>.
```

### `<samp>`

- Define a saída de um programa ou script.
- Usado para mostrar resultados ou exemplos de saída.

```html
<samp>Resultado: 42</samp>
```

### `<kbd>`

- Define entrada de teclado.
- Mostra teclas pressionadas.

```html
Pressione <kbd>Ctrl</kbd>+<kbd>C</kbd> para copiar.
```

### `<sub>` e `<sup>`

- `<sub>` define texto subscrito (abaixo da linha de base).
- `<sup>` define texto sobrescrito (acima da linha de base).

```html
H<sub>2</sub>O (água)
E=mc<sup>2</sup> (equação famosa)
```

### `<i>`

- Define texto em itálico.
- Usado para ênfase ou estilo.

```html
<i>Texto em itálico</i>
```

### `<b>`

- Define texto em negrito.
- Usado para ênfase ou estilo.

```html
<b>Texto em negrito</b>
```

### `<u>`

- Define texto sublinhado.
- Geralmente usado para links não visitados.

```html
<u>Texto sublinhado</u>
```

### `<mark>`

- Define um trecho de texto marcado.
- Usado para destacar partes do texto.

```html
<mark>Texto marcado</mark>
```