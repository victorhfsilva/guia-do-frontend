# Seletores e Consulta de Elementos no React Testing Library

## Seletores Básicos:

- **getByText**: Seleciona um elemento com base no texto que ele contém.
  ```javascript
  const element = getByText('Clique Aqui');
  // <button>Clique Aqui</button>
  ```

- **getByTestId**: Seleciona um elemento com base em um atributo `data-testid`.
  ```javascript
  const element = getByTestId('meu-elemento');
  // <div data-testid="meu-elemento">Meu Elemento</div>
  ```

- **getByLabelText**: Seleciona um elemento de formulário com base em seu rótulo.
  ```javascript
  const element = getByLabelText('Nome:');
  // <label for="name">Nome:</label> <input id="name" />
  ```

- **getByPlaceholderText**: Seleciona um elemento de input com base em seu texto de placeholder.
  ```javascript
  const element = getByPlaceholderText('Digite seu nome');
  // <input placeholder="Digite seu nome" />
  ```

- **getByAltText**: Seleciona um elemento com base em seu texto de atributo `alt`.
  ```javascript
  const element = getByAltText('Logo');
  // <img alt="Logo" src="logo.png" />
  ```

## Seletores de Consulta Múltipla:

- **getAllByText**: Seleciona todos os elementos que contêm o texto especificado.
  ```javascript
  const elements = getAllByText('Item de Lista');
  // <li>Item de Lista</li>, <li>Item de Lista</li>, ...
  ```

- **queryByText**: Retorna o primeiro elemento encontrado com o texto especificado, ou null se nenhum for encontrado.
  ```javascript
  const element = queryByText('Texto');
  // <div>Texto</div>
  ```

- **queryAllByText**: Retorna todos os elementos encontrados com o texto especificado, ou uma lista vazia se nenhum for encontrado.
  ```javascript
  const elements = queryAllByText('Texto');
  // <span>Texto</span>, <p>Texto</p>, ...
  ```

## Consulta de Elementos Específicos:

- **findByText**: Retorna uma Promise que resolve quando o elemento com o texto especificado é encontrado.
  ```javascript
  const element = await findByText('Texto Assíncrono');
  // <div>Texto Assíncrono</div>
  ```

- **findByTestId**: Retorna uma Promise que resolve quando o elemento com o atributo `data-testid` especificado é encontrado.
  ```javascript
  const element = await findByTestId('meu-elemento');
  // <div data-testid="meu-elemento">Meu Elemento</div>
  ```

## Consultas Alternativas:

- **queryBy**: Consulta um elemento por um seletor CSS arbitrário.
  ```javascript
  const element = queryBy('.classe-do-elemento');
  // <div class="classe-do-elemento"></div>
  ```

- **queryAllBy**: Consulta todos os elementos por um seletor CSS arbitrário.
  ```javascript
  const elements = queryAllBy('.classe-do-elemento');
  // <div class="classe-do-elemento"></div>, <div class="classe-do-elemento"></div>, ...
  ```
