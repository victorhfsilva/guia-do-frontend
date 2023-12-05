# Reset CSS

## O que é um Reset CSS?

Um **Reset CSS** é um conjunto de estilos CSS que redefine as configurações padrão de estilo do navegador para garantir uma base consistente e neutra para o seu projeto web. Isso ajuda a evitar comportamentos inesperados e incompatibilidades entre navegadores, permitindo que você construa sua própria estilização de forma mais consistente.

## Usando Reset CSS

Existem várias opções de Reset CSS disponíveis. Aqui está um exemplo de um Reset CSS simples:

```css
/* Reset CSS */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
}

/* Adicione suas estilizações personalizadas abaixo desta linha */
```

- `*`: Define margem e preenchimento para zero, e usa `box-sizing: border-box` para garantir que a largura e a altura incluam a borda e o preenchimento.
- `body`: Define a família de fontes e o espaçamento de linha padrão.

## Importando um Reset CSS

Você pode optar por criar seu próprio Reset CSS ou usar um existente. Um dos Resets CSS populares é o **Normalize.css**. Para usá-lo, você pode fazer o seguinte:

1. Baixe o arquivo Normalize.css do [site oficial](https://necolas.github.io/normalize.css/).

2. Adicione o arquivo Normalize.css à sua pasta de projeto.

3. Importe o Normalize.css no seu arquivo CSS principal:

```css
/* No seu arquivo CSS principal (por exemplo, style.css) */
@import "normalize.css";

/* Adicione suas estilizações personalizadas abaixo desta linha */
```

## Conclusão

Usar um Reset CSS é uma prática comum para criar projetos web consistentes e compatíveis com navegadores. Lembre-se de que você pode personalizar seu Reset CSS para atender às necessidades específicas do seu projeto, mas é importante manter a base neutra e consistente fornecida pelo Reset. Isso ajuda a economizar tempo e evitar surpresas desagradáveis durante o desenvolvimento.