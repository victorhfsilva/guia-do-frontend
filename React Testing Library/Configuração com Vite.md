# Configurando o React Testing Library com Vite

## 1. Instalação das dependências

```bash
npm install jest --save-dev
npm install @testing-library/react --save-dev
npm install ts-jest @types/jest --save-dev
```

## 2. Edite o arquivo package.json

Adicione `"test": "jest"` nos scripts do package.json.

Exemplo:

```json
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview",
    "test": "jest"
  }
```

## 3. Instalação de mais dependências

```bash
npm install ts-node @testing-library/jest-dom --save-dev
npm install jest-environment-jsdom
npm install identity-obj-proxy --save-dev
```

## 4. Crie o arquivo jest.config.ts

Crie o arquivo jest.config.ts na pasta root com o seguinte conteúdo:

```ts
export default {
    preset: 'ts-jest',
    testEnvironment: 'jest-environment-jsdom',
    transform: {
        "^.+\\.tsx?$": "ts-jest" 
    // process `*.tsx` files with `ts-jest`
    },
    moduleNameMapper: {
        '\\.(gif|ttf|eot|svg|png)$': '<rootDir>/fileMock.js',
        "^.+\\.svg$": "jest-svg-transformer",
        "^.+\\.(css|less|scss)$": "identity-obj-proxy"
    },
}
```

## 5. Crie o arquivo fileMock.js

Crie o arquivo fileMock.js na pasta root com o seguinte conteúdo:

```js
module.exports = {
    __esModule: true,
    default: 'test-file-stub',
};
```

## 6. Edite o arquivo .eslintrc.cjs

Adicione `"react-app", "react-app/jest"` no array extends da configuração.

Exemplo:

```js
module.exports = {
  root: true,
  env: { browser: true, es2020: true },
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended',
    'plugin:react-hooks/recommended',
    "react-app", "react-app/jest"
  ],
  ignorePatterns: ['dist', '.eslintrc.cjs'],
  parser: '@typescript-eslint/parser',
  plugins: ['react-refresh'],
  rules: {
    'react-refresh/only-export-components': [
      'warn',
      { allowConstantExport: true },
    ],
  },
}
```

## 7. Importe as dependências necessárias nos testes

No arquivo App.spec.tsx:

```tsx
import '@testing-library/jest-dom'
import { render } from "@testing-library/react"
import App from "../App"

test("Renders the main page", () => {
    render(<App />)
    expect(true).toBeTruthy()
})
```


