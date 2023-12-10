# Promises em JavaScript

As Promises são uma maneira de lidar com tarefas assíncronas em JavaScript de uma forma mais organizada e compreensível.

## Criando uma Promise

```javascript
const minhaPromise = new Promise((resolve, reject) => {
  // Dentro desta função, você realiza sua operação assíncrona.  
  if (sucesso) {
    // Se for bem-sucedida, chame resolve com o resultado.
    resolve(resultado); // Quando a operação é bem-sucedida
  } else {
    // Se houver um erro, chame reject com o motivo do erro.
    reject(erro); // Quando ocorre um erro
  }
});
```

### Exemplo:

```javascript
const randomNumberPromise = new Promise((resolve, reject) => {
    setTimeout(() => {
        const number = parseInt(Math.random()*100);
        resolve(number)
    }, 1000);
});
```

## Tratando o Resultado de uma Promise

```javascript
minhaPromise
  .then(resultado => {
    // Tratar o resultado bem-sucedido
  })
  .catch(erro => {
    // Tratar o erro
  })
  .finally(() => {
    // Será executado independentemente de sucesso ou erro
  });
```

### Exemplo:

```javascript
randomNumberPromise
    .then((value) => {
        console.log(value);
    })
    .catch((error) => {
        console.log(error);
    })
    .finally(() => {
        console.log(error)
    });
```

## Encadeando Promises

Você pode encadear várias Promises juntas para executar tarefas em sequência.

```javascript
minhaPromise
  .then(resultado1 => {
    return outraPromise(resultado1);
  })
  .then(resultado2 => {
    // Faça algo com resultado2
  })
  .catch(erro => {
    // Lidar com erros em qualquer parte da cadeia
  });
```

## Promise.all

Use `Promise.all` quando precisar esperar várias Promises serem resolvidas antes de continuar.

```javascript
const promessas = [promise1, promise2, promise3];

Promise.all(promessas)
  .then(resultados => {
    // Array de resultados quando todas as Promises forem resolvidas
  })
  .catch(erro => {
    // Lidar com o primeiro erro encontrado
  });
```

## Promise.race

`Promise.race` é útil quando você quer receber o resultado da primeira Promise que for resolvida.

```javascript
const promessas = [promise1, promise2, promise3];

Promise.race(promessas)
  .then(resultado => {
    // Trate o resultado da primeira Promise resolvida
  })
  .catch(erro => {
    // Lidar com o erro da primeira Promise rejeitada
  });
```

## Funções Assíncronas

As funções assíncronas, declaradas com `async`, tornam mais fácil o uso de Promises.

```javascript
async function minhaFuncaoAsync() {
  try {
    const resultado = await minhaPromise;
    // Faça algo com o resultado
  } catch (erro) {
    // Lidar com erros
  }
}
```

### Await

- `await` só pode ser utilizado dentro de uma função `async`.
- Ele é utilizado para pausar a execução da função até que uma promise seja resolvida.

```javascript
async function getGithubUser(username) { // promise + await keyword usage allowed
  const response = await fetch(`https://api.github.com/users/${username}`); // Execution stops here until fetch promise is fulfilled
  return response.json();
}

getGithubUser('victorhfsilva')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

### Exemplo de Uso: Fetch API

```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Erro na requisição');
    }
    return response.json();
  })
  .then(data => {
    // Tratar os dados
  })
  .catch(erro => {
    // Lidar com erros de rede ou do servidor
  });
```

### Exemplo de Uso: Leitura de arquivo

```javascript
const fs = require('fs');
const path = require('path');

const filePath = path.resolve(__dirname, 'tasks.csv');

const fileReadPromise = fs.promises.readFile(filePath);

fileReadPromise
    .then((file) => file.toString('utf8'))
    .then((text) => text.split('\n').slice(1))
    .then((lines) => lines.map((lines) => {
        const [name, done] = linha.split(';');
        return {
            name,
            done: done.trim() === 'true'
        }
    }))
    .then((tasksList) => console.log(tasksList))
    .catch((error) => console.log(error));
```

Ou,

```javascript
const fs = require('fs');
const path = require('path');

const filePath = path.resolve(__dirname, 'tasks.csv');

async function buscarArquivo() {
    try {
        const fileReadPromise = await fs.promises.readFile(filePath); 
        const text = file.toString('utf8');
        const lines = text.split('\n').slice(1));
        const tasksList = lines.map((lines) => {
            const [name, done] = linha.split(';');
            return {
                name,
                done: done.trim() === 'true'
            };
        console.log(tasksList);
    } catch (error) {
        console.log(error);
    }
}
```
Promises são valiosas para lidar com operações assíncronas em JavaScript. Elas tornam seu código mais organizado e fácil de entender.