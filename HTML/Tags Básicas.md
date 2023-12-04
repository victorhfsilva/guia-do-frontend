# Tags HTML5 Básicas

## Divisão em Seções
```html
<header>: Define o cabeçalho.
<main>: Define o conteúdo principal.
<section>: Define uma seção.
<article>: Define um artigo.
<footer>: Define um rodapé
<aside>: Define uma seção lateral.
<div>: Define uma divisão em containers em nível de blocos.
<span>: Define uma divisão em containers em nível de linha.
```

## Tags de Texto e Estilo
```html
<h1>, <h2>, ...: Títulos
<a>: Link, junto ao atributo href.
<strong>: Texto em negrito.
<em>: Texto em itálico.
<mark>: Destacar texto.
<abbr>: Abreviação ou acrônimo.
<code>: Código de programação.
<pre>: Texto pré-formatado.
<cite>: Citação.
<q>: Citação curta.
<sup>: Texto sobrescrito.
<sub>: Texto subscrito.
<del>: Texto deletado.
<ins>: Texto inserido.
```

## Multimídia
```html
<img>: Inserir imagens.
<audio>: Inserir áudio.
<video>: Inserir vídeo.
<iframe>: Inserir conteúdo externo (como vídeos do YouTube).
```
## Listas e Tabelas
```html
<ul>: Lista não ordenada.
<ol>: Lista ordenada.
<li>: Item de lista.
<dl>: Lista de definição.
<dt>: Termo de definição.
<dd>: Descrição de definição.
<table>: Tabela.
<tr>: Linha da tabela.
<th>: Cabeçalho da tabela.
<td>: Célula da tabela.
```
## Formulários
```html
<form>: Formulário.
<input>: Campo de entrada.
<textarea>: Área de texto.
<button>: Botão.
<select>: Caixa de seleção.
<label>: Rótulo para elementos do formulário.
<fieldset>: Agrupamento de campos.
<legend>: Legenda para um <fieldset>.
```

## Exemplo

```html
<!DOCTYPE html> <!-- Define o tipo de documento como HTML5 -->
<html lang="pt-BR"> <!-- Define o elemento raiz da página e a linguagem padrão -->
<head>
    <meta charset="UTF-8"> <!-- Define o conjunto de caracteres da página como UTF-8 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- Configuração da viewport para dispositivos móveis -->
    <title>Título da Página</title> <!-- Define o título da página exibido na aba do navegador -->
    <link rel="stylesheet" href="styles.css"> <!-- Conexão com um arquivo de folha de estilos externo -->
</head>
<body>
    <!-- Cabeçalho -->
    <header>
        <h1>Título Principal</h1> <!-- Título principal da página -->
        <nav>
            <ul>
                <li><a href="#">Início</a></li> <!-- Lista de links de navegação -->
                <li><a href="#">Sobre</a></li>
                <li><a href="#">Serviços</a></li>
                <li><a href="#">Contato</a></li>
            </ul>
        </nav>
    </header>
    <!-- Conteúdo Principal -->
    <main>
        <article>
            <h2>Título do Artigo</h2> <!-- Título do artigo -->
            <p>Este é um parágrafo no artigo.</p> <!-- Parágrafo de texto -->
            <a href="#">Leia mais</a> <!-- Link para ler mais conteúdo -->
        </article>

        <section>
            <h3>Seção 1</h3>
            <p>Conteúdo da Seção 1.</p>
        </section>

        <section>
            <h3>Seção 2</h3>
            <p>Conteúdo da Seção 2.</p>
        </section>
    </main>
    <!-- Rodapé -->
    <footer>
        <p>&copy; 2023 Nome da Empresa</p> <!-- Rodapé da página com direitos autorais -->
    </footer>
</body>
</html>
```


Essas são apenas algumas das muitas tags HTML5 disponíveis para criar páginas web. Cada uma tem um propósito específico e pode ser combinada para criar layouts e conteúdos complexos. A escolha das tags a serem usadas depende do conteúdo e da estrutura da sua página.