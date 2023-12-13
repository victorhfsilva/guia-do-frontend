# Como configurar o arquivo `tsconfig.json`:

O arquivo `tsconfig.json` é usado para configurar as opções de compilação e o comportamento do compilador TypeScript (tsc) em seu projeto.

## Criando um Arquivo `tsconfig.json`

Você pode criar um arquivo `tsconfig.json` manualmente ou gerá-lo com o seguinte comando:

```bash
tsc --init
```

Isso criará um arquivo de configuração padrão com várias opções. Você pode personalizá-lo de acordo com as necessidades do seu projeto.

## Exemplo de um `tsconfig.json` Simples

Aqui está um exemplo de um `tsconfig.json` simples:

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "CommonJS",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

Vamos dar uma olhada nas opções mais comuns:

- `compilerOptions`: Aqui você pode definir várias opções de compilação. Algumas das opções comuns incluem:

  - `target`: A versão do ECMAScript para a qual você está compilando (por exemplo, "ESNext", "ES2019").
  - `module`: O sistema de módulos a ser usado (por exemplo, "CommonJS", "ES6").
  - `outDir`: O diretório de saída onde os arquivos JavaScript serão gerados.
  - `rootDir`: O diretório raiz onde seus arquivos TypeScript estão localizados.
  - `strict`: Ativa várias verificações estritas do TypeScript.

- `include`: Uma matriz de padrões de inclusão que especifica quais arquivos TypeScript devem ser incluídos na compilação.

- `exclude`: Uma matriz de padrões de exclusão que especifica quais diretórios ou arquivos devem ser excluídos da compilação.

### Organização do Projeto

Ao definir a estrutura de diretórios e arquivos em seu projeto, é importante alinhar o `rootDir` e a configuração `include` no `tsconfig.json` para garantir que todos os arquivos desejados sejam incluídos na compilação.

### Documentação Completa

A documentação completa com todas as opções disponíveis pode ser encontrada no site oficial do TypeScript: [tsconfig.json documentation](https://www.typescriptlang.org/tsconfig).

Lembre-se de que a configuração do `tsconfig.json` é altamente dependente das necessidades do seu projeto. Certifique-se de ajustar as opções de acordo com os requisitos específicos do seu projeto.

