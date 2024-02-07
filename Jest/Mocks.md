# Mocks no Jest

#### 1. Criando Mocks Simples

```javascript
// Criando um mock simples substituindo uma função com uma implementação simulada.
const minhaFuncao = jest.fn();
```

#### 2. Criando Mocks com Implementação Personalizada

```javascript
// Criando um mock com uma implementação personalizada.
const minhaFuncao = jest.fn(() => 'retorno personalizado');
```

#### 3. Mockando Módulos Inteiros

```javascript
// Criando um mock para um módulo inteiro.
jest.mock('./meuModulo');
```

#### 4. Restaurando Mocks

```javascript
// Restaurando um mock para sua implementação original.
jest.restoreAllMocks();
```

#### 5. Mockando Funções com Implementações Diferentes

```javascript
// Mockando uma função com diferentes implementações em chamadas sequenciais.
const minhaFuncao = jest.fn()
  .mockImplementationOnce(() => 'primeira chamada')
  .mockImplementationOnce(() => 'segunda chamada');
```

#### 6. Mockando Métodos de Objeto

```javascript
// Mockando um método de um objeto.
const meuObjeto = { metodo: () => {} };
const spy = jest.spyOn(meuObjeto, 'metodo');
```

#### 7. Encadeando Mocks

```javascript
// Encadeando mocks para métodos de um objeto.
const meuObjeto = {
  metodo1: () => {},
  metodo2: () => {}
};
jest.spyOn(meuObjeto, 'metodo1').mockReturnValue('retorno do método 1');
jest.spyOn(meuObjeto, 'metodo2').mockReturnValue('retorno do método 2');
```

#### 8. Mockando Módulos Externos

```javascript
// Mockando um módulo externo e sua implementação.
jest.mock('meu-modulo-externo', () => ({
  minhaFuncaoExterna: jest.fn(() => 'retorno do módulo externo')
}));
```

#### 9. Mockando Construtores de Classes

```javascript
// Mockando o construtor de uma classe.
jest.mock('./MinhaClasse', () => {
  return jest.fn().mockImplementation(() => {
    return {
      metodo: () => 'retorno do método'
    };
  });
});
```

#### 10. Observando Chamadas

```javascript
// Observando chamadas de uma função ou método.
const minhaFuncao = jest.fn();
minhaFuncao();
expect(minhaFuncao).toHaveBeenCalled();
```

#### 11. Testando Parâmetros de Entrada

```javascript
// Testando parâmetros passados para uma função.
const minhaFuncao = jest.fn();
minhaFuncao('arg1', 'arg2');
expect(minhaFuncao).toHaveBeenCalledWith('arg1', 'arg2');
```

#### 12. Mockando Múltiplas Funções com Implementações Diferentes

```javascript
// Mockando múltiplas funções com diferentes implementações.
const minhaFuncao1 = jest.fn(() => 'retorno da função 1');
const minhaFuncao2 = jest.fn(() => 'retorno da função 2');
```

#### 13. Restaurando Mocks Individuais

```javascript
// Restaurando um mock específico para sua implementação original.
jest.resetAllMocks(); // Restaura todos os mocks
minhaFuncao.mockRestore(); // Restaura apenas o mock `minhaFuncao`
```

#### 14. Mockando Funções Assíncronas

```javascript
// Mockando uma função assíncrona com uma implementação personalizada.
const minhaFuncaoAssincrona = jest.fn().mockResolvedValue('valor resolvido');
```

#### 15. Testando Chamadas em Ordem

```javascript
// Testando chamadas em uma ordem específica.
const minhaFuncao = jest.fn();
minhaFuncao();
minhaFuncao('arg1');
expect(minhaFuncao).toHaveBeenNthCalledWith(1);
expect(minhaFuncao).toHaveBeenNthCalledWith(2, 'arg1');
```

---

Com este cheatsheet detalhado e repleto de exemplos, você deve ser capaz de criar mocks eficazes para testar seu código de forma completa e precisa usando o Jest. Lembre-se de adaptar essas técnicas conforme necessário para atender às necessidades específicas dos seus casos de teste.