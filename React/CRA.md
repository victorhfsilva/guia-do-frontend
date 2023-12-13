# Inicializando Projetos com React

O React é uma biblioteca JavaScript popular para criar interfaces de usuário interativas e reativas. Este cheatsheet oferece uma visão geral dos passos fundamentais para criar um projeto React.

### Instale o Create React App (CRA)

O Create React App é uma ferramenta que facilita a criação e configuração inicial de projetos React.

```bash
npx create-react-app meu-projeto
```

Ou para inicializar projetos em Typescript:

```bash
npx create-react-app my-app --template typescript
```

```bash
yarn create react-app testing-react --template typescript
```

### Execute o Projeto

Navegue até a pasta do projeto e inicie o servidor de desenvolvimento.

```bash
npm start
```

Isso abrirá seu aplicativo React no navegador e atualizará automaticamente as alterações em tempo real.

### Build de Produção

Quando estiver pronto para implantar, crie uma versão de produção do seu aplicativo.

```bash
npm run build
```

Isso criará uma pasta `build/` com os arquivos otimizados para produção.

### Implantação

Implante seu aplicativo em um servidor ou plataforma de hospedagem. Serviços populares incluem Netlify, Vercel, AWS Amplify e GitHub Pages.

