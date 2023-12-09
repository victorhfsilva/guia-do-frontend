# Introdução ao Sass

Sass (Syntactically Awesome Stylesheets) é uma linguagem de extensão para folhas de estilo CSS que adiciona recursos poderosos e facilita a escrita e manutenção de código CSS. 

## O que é Sass?

O Sass é uma linguagem de script que é interpretada ou compilada em CSS. Ele introduz recursos como variáveis, aninhamento, mixins e outras funcionalidades que não estão presentes no CSS tradicional. O código Sass é mais conciso, modular e facilita a manutenção de estilos em projetos web.

### Características Principais:

- **Variáveis:** Defina variáveis para armazenar valores reutilizáveis.
- **Aninhamento:** Aninhe seletores para representar a hierarquia de maneira mais clara.
- **Mixins:** Crie blocos de código reutilizáveis e parametrizáveis.
- **Herança:** Compartilhe estilos entre seletores usando herança.
- **Importação:** Divida o código em vários arquivos e importe-os conforme necessário.

## Como Instalar e Utilizar Sass:

### 1. Instalação:

- Para instalar o SASS basta:

    ```bash
    npm install -D sass
    ```

- Ou para instalar globalmente:

    ```bash
    npm install -g sass
    ```

### 2. Compilação:

- **Compilar Arquivos Sass para CSS:**

    ```bash
    sass input.scss output.css
    ```

- **Observar Mudanças e Compilar Automaticamente:**

    ```bash
    sass --watch input.scss:output.css
    ```

### 3. Sintaxe Básica:

- **Variáveis:**

    ```scss
    $cor-primaria: #3498db;
    body {
        background-color: $cor-primaria;
    }
    ```

- **Aninhamento:**

    ```scss
    nav {
        ul {
            margin: 0;
            padding: 0;
            list-style: none;

            li { display: inline-block; }

            a {
                text-decoration: none;
                display: block;
                padding: 6px 12px;
            }
        }
    }
    ```

- **Mixins:**

    ```scss
    @mixin texto-centralizado {
        text-align: center;
        vertical-align: middle;
        line-height: 1.5;
    }

    .destaque {
        @include texto-centralizado;
        font-size: 18px;
        color: #ff0000;
    }
    ```

- **Herança:**

    ```scss
    .botao {
        padding: 10px;
        border: 1px solid #ccc;
        background-color: #f0f0f0;
    }

    .botao-destaque {
        @extend .botao;
        background-color: #ff0000;
        color: #fff;
    }
    ```

- **Importação:**

    ```scss
    // arquivo1.scss
    $cor-destaque: #ff0000;
    
    // arquivo2.scss
    @import 'arquivo1';
    
    .elemento {
        color: $cor-destaque;
    }
    ```

O Sass oferece uma sintaxe mais avançada e recursos poderosos que facilitam a escrita de estilos CSS mais eficientes e flexíveis. Ao integrar o Sass em seus projetos, considere as melhores práticas e explore os recursos adicionais para otimizar seu fluxo de trabalho de desenvolvimento front-end.