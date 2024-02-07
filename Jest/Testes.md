# Instalação e Configuração Inicial

## Instale o Jest como dependência de desenvolvimento:
   ```sh
   npm install jest --save-dev
   ```

## Configure o Jest no arquivo `package.json`:
   ```json
   "scripts": {
       "test": "jest"
   }
   ```

## Escrevendo Testes Básicos

### Importe as funções e módulos necessários:

   ```javascript
   import { FuncaoTestada } from "./seu-arquivo.js";
   ```

### Escreva testes usando a função `test` ou `it`:

   ```javascript
   test("Descrição do teste", () => {
       // Código de teste
   });

   // Ou usando 'it':
   it("Descrição do teste", () => {
       // Código de teste
   });
   ```

### Teste Assíncrono:

   ```javascript
   test("Teste assíncrono", async () => {
       const resultado = await FuncaoAssincrona();
       expect(resultado).toBe(valorEsperado);
   });
   ```
   
Ou,

   ```javascript
   test("Teste assíncrono", async () => {
       await expect(FuncaoAssincrona()).resolves.toBe(valorEsperado);
   });
   ```

### Teste de Exceção:

   ```javascript
   test("Teste de exceção", () => {
       expect(() => FuncaoQueDeveLancarExcecao()).toThrow(ErrorEsperado);
   });
   ```

### Teste de Mock:

   ```javascript
   // Crie um mock de função
   const mockFuncao = jest.fn();

   // Configure o comportamento do mock
   mockFuncao.mockReturnValue(valor);

   // Verifique se o mock foi chamado
   expect(mockFuncao).toHaveBeenCalled();
   ```

## Rodando Testes:

Execute os testes usando o comando:
```sh
npm test
```

### Resultados:

O Jest exibirá os resultados dos testes no terminal, indicando testes passados, falhos ou pendentes.