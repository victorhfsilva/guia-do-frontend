# TypeScript Compiler (tsc):

## Compilação Básica

Para compilar um arquivo TypeScript, basta executar o seguinte comando no terminal:

```bash
tsc nome-do-arquivo.ts
```

Isso gerará um arquivo JavaScript equivalente com a extensão `.js`. Se você estiver usando TypeScript com React, você pode compilar arquivos `.tsx` da mesma maneira.

### Compilação de Múltiplos Arquivos

Para compilar vários arquivos TypeScript de uma vez, você pode usar o seguinte comando:

```bash
tsc arquivo1.ts arquivo2.ts arquivo3.ts
```

Isso gerará arquivos JavaScript correspondentes para cada arquivo TypeScript fornecido.

### Compilação Automática
Para compilar automaticamente os arquivos TypeScript quando houver alterações, você pode usar o modo "watch" do tsc:

```bash
tsc -w
```

Isso manterá o tsc em execução e recompilará seus arquivos sempre que houver alterações.

### Erros e Avisos
O TypeScript Compiler fornecerá informações detalhadas sobre erros e avisos encontrados em seu código. Certifique-se de ler as mensagens de erro cuidadosamente para corrigir problemas em seu código.

## Configuração com tsconfig.json

Para projetos maiores, é aconselhável criar um arquivo de configuração [tsconfig.json](./tsconfig.md). Isso permite que você configure as opções de compilação de forma centralizada. Você pode gerar um arquivo `tsconfig.json` usando o comando:

```bash
tsc --init
```

Depois disso, você pode personalizar as opções no `tsconfig.json`, como definir o diretório de saída, especificar quais arquivos incluir ou excluir e muito mais.

