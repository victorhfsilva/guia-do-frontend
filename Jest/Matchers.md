# Matchers

## 1. Verificando Valores

- **`toBe(valor)`**: Compara se dois valores são estritamente iguais (usando `===`).
  ```javascript
  expect(resultado).toBe(42);
  ```

- **`toEqual(valor)`**: Compara se dois valores são iguais, recursivamente.
  ```javascript
  expect(array).toEqual([1, 2, 3]);
  ```

- **`toBeNull()`**: Verifica se o valor é `null`.
  ```javascript
  expect(valor).toBeNull();
  ```

- **`toBeDefined()`**: Verifica se o valor é definido (não é `undefined`).
  ```javascript
  expect(valor).toBeDefined();
  ```

## 2. Verificando Tipos

- **`toBeInstanceOf(Classe)`**: Verifica se um objeto é uma instância de uma classe.
  ```javascript
  expect(objeto).toBeInstanceOf(MinhaClasse);
  ```

- **`typeof tipo`**: Verifica se o tipo de um valor é o esperado.
  ```javascript
  expect(typeof valor).toBe('number');
  ```

## 3. Verificando Exceções

- **`toThrow()`**: Verifica se uma função lança uma exceção.
  ```javascript
  expect(() => { throw new Error('Erro!'); }).toThrow();
  ```

- **`toThrowError(mensagem?)`**: Verifica se uma função lança uma exceção com uma mensagem específica.
  ```javascript
  expect(função).toThrowError('Mensagem de Erro');
  ```

## 4. Outras Opções

- **`toBeGreaterThan(valor)`**: Verifica se um valor é maior que outro.
  ```javascript
  expect(10).toBeGreaterThan(5);
  ```

- **`toBeLessThan(valor)`**: Verifica se um valor é menor que outro.
  ```javascript
  expect(5).toBeLessThan(10);
  ```

- **`toContain(valor)`**: Verifica se um array ou string contém um determinado valor.
  ```javascript
  expect(array).toContain(42);
  ```

- **`toBeCalled()`**: Verifica se uma função foi chamada (útil para spies).
  ```javascript
  expect(função).toBeCalled();
  ```

## 5. Modificadores

- **`.not`**: Inverte o resultado da asserção.
  ```javascript
  expect(valor).not.toBeFalsy();
  ```

- **`.toThrowErrorMatchingSnapshot()`**: Verifica se uma exceção corresponde ao snapshot.
  ```javascript
  expect(função).toThrowErrorMatchingSnapshot();
  ```

## 6. Verificando a Presença no Documento

- **`toBeInTheDocument()`**: Verifica se o elemento está presente no documento.
  ```javascript
  expect(elemento).toBeInTheDocument();
  ```

- **`toBeVisible()`**: Verifica se o elemento está visível para o usuário (não oculto por CSS, por exemplo).
  ```javascript
  expect(elemento).toBeVisible();
  ```

- **`toBeEmpty()`**: Verifica se o elemento não contém nenhum texto ou elementos filhos.
  ```javascript
  expect(elemento).toBeEmpty();
  ```

## 7. Verificando Estilos e Classes

- **`toHaveStyle(estilo)`**: Verifica se o elemento tem o estilo especificado.
  ```javascript
  expect(elemento).toHaveStyle('color: red');
  ```

- **`toHaveClass(classe)`**: Verifica se o elemento tem a classe especificada.
  ```javascript
  expect(elemento).toHaveClass('ativo');
  ```

## 8. Verificando Propriedades

- **`toHaveAttribute(atributo, valor?)`**: Verifica se o elemento tem o atributo especificado e opcionalmente verifica seu valor.
  ```javascript
  expect(elemento).toHaveAttribute('href', 'https://www.exemplo.com');
  ```

- **`toHaveTextContent(texto)`**: Verifica se o elemento contém o texto especificado.
  ```javascript
  expect(elemento).toHaveTextContent('Bem-vindo!');
  ```

## 9. Verificando Hierarquia

- **`toContainElement(elemento)`**: Verifica se o elemento contém um elemento filho especificado.
  ```javascript
  expect(container).toContainElement(botao);
  ```

- **`toContainHTML(html)`**: Verifica se o elemento contém uma determinada marcação HTML.
  ```javascript
  expect(container).toContainHTML('<button>Enviar</button>');
  ```

## 10. Matchers Personalizados

Você também pode criar seus próprios matchers personalizados para estender as capacidades do `expect`.

```javascript
expect.extend({
  toBeDivisívelPor(recebido, divisor) {
    const pass = recebido % divisor === 0;
    if (pass) {
      return {
        message: () => `Esperava que ${recebido} não fosse divisível por ${divisor}`,
        pass: true,
      };
    } else {
      return {
        message: () => `Esperava que ${recebido} fosse divisível por ${divisor}`,
        pass: false,
      };
    }
  },
});

expect(10).toBeDivisívelPor(5);
```