# Configuração do Jest e React Testing Library com Vite

Criar testes para suas aplicações React é uma prática essencial para garantir a qualidade e a estabilidade do código ao longo do tempo. Jest e React Testing Library são ferramentas poderosas que, quando combinadas, proporcionam um ambiente de teste robusto para seus projetos React. Neste guia, vamos configurar o Jest e o React Testing Library em um projeto criado com Vite.

### Passo 1: Instalar Dependências

Inicialmente, é necessário instalar o Jest, as tipagens para o Jest (se você estiver usando TypeScript), e o React Testing Library. Abra o terminal no diretório do seu projeto e execute os seguintes comandos:

1. Instalar Jest e @types/jest:
```bash
npm install jest @types/jest -D
```

2. Instalar o React Testing Library e suas dependências:
```bash
npm install @testing-library/jest-dom @testing-library/react @testing-library/user-event -D
```

3. Para transpilar código JSX e TypeScript, instale o Babel, suas presets e jest-environment-jsdom:
```bash
npm install @babel/core @babel/preset-env @babel/preset-react babel-jest identity-obj-proxy jest-environment-jsdom -D
```

4. Por fim, instale a preset do TypeScript para o Babel:
```bash
npm install --save-dev @babel/preset-typescript
```

### Passo 2: Configurar o Jest

1. **Adicionar Script de Teste** no seu `package.json`:
```json
"scripts": {
  "test": "jest"
}
```
Isso permite que você execute seus testes usando o comando `npm test`.

2. **Configuração do Jest**: No seu `package.json`, adicione a seguinte configuração do Jest:
```json
"jest": {
  "testEnvironment": "jest-environment-jsdom",
  "setupFilesAfterEnv": ["<rootDir>/setup-tests.js"]
}
```
Essa configuração define o ambiente de teste para simular um ambiente de navegador (usando jsdom) e especifica um arquivo de configuração que será executado após o ambiente de teste ser configurado.

### Passo 3: Arquivo de Configuração dos Testes

Crie um arquivo chamado `setup-tests.js` na raiz do seu projeto. Este arquivo será utilizado para importar qualquer configuração global ou extensões necessárias para os testes. Adicione a seguinte linha:

```js
import '@testing-library/jest-dom';
```

Isso irá automaticamente importar as extensões do jest-dom cada vez que seus testes forem executados, proporcionando matchers adicionais (como `.toBeVisible()`).

### Passo 4: Configurar o ESLint

Para que o ESLint entenda e não marque como erros as características específicas do ambiente Node.js, adicione ao seu arquivo `.eslintrc.cjs`:

```json
"env": {
    "node": true
}
```

### Passo 5: Configurar o Babel

Crie um arquivo chamado `babel.config.js` na raiz do seu projeto e adicione a seguinte configuração:

```js
module.exports = {
    presets: [
        ['@babel/preset-env', { targets: { esmodules: true } }],
        ['@babel/preset-react', { runtime: 'automatic' }],
        '@babel/preset-typescript'
    ]
};
```

Isso configura o Babel para transpilar código JavaScript moderno, React JSX e TypeScript.

### Conclusão

Após seguir esses passos, seu projeto estará configurado para utilizar o Jest e o React Testing Library para testes. Essa configuração permite que você escreva e execute testes para seus componentes React de forma eficiente, contribuindo para uma base de código mais estável e confiável. Lembre-se de sempre escrever testes para novos componentes e funcionalidades, garantindo assim que suas alterações não quebrem funcionalidades existentes.