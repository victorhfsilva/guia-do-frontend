## Mocks no React

Mocks são úteis em testes para isolar a lógica da aplicação das dependências externas. 

### Mockando Serviços

#### Usando `jest.mock()`

Para mockar serviços que fazem chamadas HTTP, você pode usar `jest.mock()`.

```javascript
// service.js
export const fetchData = async () => {
  const response = await fetch('/api/data');
  return response.json();
};

// service.test.js
import { fetchData } from './service';

jest.mock('./service');

test('fetchData returns mocked data', async () => {
  fetchData.mockResolvedValue({ data: 'mocked data' });

  const result = await fetchData();
  expect(result.data).toBe('mocked data');
});
```

### Mockando Hooks

#### Usando `jest.mock()` para hooks personalizados

```javascript
// useCustomHook.js
import { useState, useEffect } from 'react';

export const useCustomHook = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then((response) => response.json())
      .then(setData);
  }, []);

  return data;
};

// component.test.js
import { renderHook } from '@testing-library/react-hooks';
import { useCustomHook } from './useCustomHook';

jest.mock('./useCustomHook');

test('useCustomHook returns mocked data', () => {
  useCustomHook.mockReturnValue('mocked data');

  const { result } = renderHook(() => useCustomHook());
  expect(result.current).toBe('mocked data');
});
```

### Mockando Funções

#### Usando `jest.fn()`

```javascript
// utils.js
export const add = (a, b) => a + b;

// utils.test.js
import { add } from './utils';

test('add function', () => {
  const mockAdd = jest.fn(add);

  expect(mockAdd(1, 2)).toBe(3);
  expect(mockAdd).toHaveBeenCalledWith(1, 2);
});
```

### Mockando Módulos

#### Usando `jest.mock()`

```javascript
// math.js
export const multiply = (a, b) => a * b;

// component.test.js
import { multiply } from './math';

jest.mock('./math');

test('multiply function', () => {
  multiply.mockReturnValue(10);

  expect(multiply(2, 5)).toBe(10);
});
```

### Mockando Funções Assíncronas

#### Usando `jest.mock()` com `mockResolvedValue`

```javascript
// asyncFunction.js
export const fetchData = async () => {
  const response = await fetch('/api/data');
  return response.json();
};

// asyncFunction.test.js
import { fetchData } from './asyncFunction';

jest.mock('./asyncFunction');

test('fetchData returns mocked data', async () => {
  fetchData.mockResolvedValue({ data: 'mocked data' });

  const result = await fetchData();
  expect(result.data).toBe('mocked data');
});
```

### Mockando Módulos com Funções Assíncronas

```javascript
// asyncModule.js
export const getData = async () => {
  const response = await fetch('/api/data');
  return response.json();
};

// asyncModule.test.js
import { getData } from './asyncModule';

jest.mock('./asyncModule');

test('getData returns mocked data', async () => {
  getData.mockResolvedValue({ data: 'mocked data' });

  const result = await getData();
  expect(result.data).toBe('mocked data');
});
```

###  Mockando Métodos de Objetos

#### Usando `jest.spyOn()`

```javascript
// objectMethods.js
export const obj = {
  method: () => 'real implementation',
};

// objectMethods.test.js
import { obj } from './objectMethods';

test('method is called', () => {
  const spy = jest.spyOn(obj, 'method').mockReturnValue('mocked implementation');

  expect(obj.method()).toBe('mocked implementation');
  expect(spy).toHaveBeenCalled();
});
```

### Mocks em Typescript

O `as jest.Mock` é utilizado para garantir que o TypeScript reconheça a função mockada corretamente, especialmente quando você está lidando com funções que possuem tipos complexos.

#### Service

```typescript
// service.ts
export const fetchData = async (): Promise<{ data: string }> => {
  const response = await fetch('/api/data');
  return response.json();
};

// service.test.ts
import { fetchData } from './service';

jest.mock('./service');
const mockFetchData = fetchData as jest.Mock;

test('fetchData returns mocked data', async () => {
  mockFetchData.mockResolvedValue({ data: 'mocked data' });

  const result = await fetchData();
  expect(result.data).toBe('mocked data');
});
```

#### Hook

```typescript
// useCustomHook.js
import { useState, useEffect } from 'react';

export const useCustomHook = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then((response) => response.json())
      .then(setData);
  }, []);

  return data;
};

// component.test.js
import { renderHook } from '@testing-library/react-hooks';
import { useCustomHook } from './useCustomHook';

jest.mock('./useCustomHook');
const mockUseCustomHook = useCustomHook as jest.Mock;

test('useCustomHook returns mocked data', () => {
  mockUseCustomHook.mockReturnValue('mocked data');

  const { result } = renderHook(() => mockUseCustomHook());
  expect(result.current).toBe('mocked data');
});
```

### Usando `mockClear()`

O método `mockClear()` é utilizado para limpar todas as chamadas e instâncias que foram feitas ao mock. Isso é especialmente útil em casos onde você quer garantir que o mock não tenha estado residual de testes anteriores.

```typescript
test('fetchData is called once', async () => {
  mockFetchData.mockResolvedValue({ data: 'mocked data' });

  await fetchData();
  expect(mockFetchData).toHaveBeenCalledTimes(1);

  mockFetchData.mockClear();

  await fetchData();
  expect(mockFetchData).toHaveBeenCalledTimes(1);
});
```
Também pode ser útil limpar os estados dentro de um método before each.

```typescript
beforeEach(() => {
    mockFetchData.mockClear();
});
```