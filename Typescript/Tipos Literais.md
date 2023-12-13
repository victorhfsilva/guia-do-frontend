#  Tipos Literais

Os tipos literais em objetos no TypeScript permitem especificar valores fixos para as propriedades de um objeto. Isso proporciona maior clareza e precisão ao modelar estruturas de dados com propriedades específicas.

## **Sintaxe Básica**

```typescript
type Pessoa = {
  sexo: "masculino" | "feminino";
  estadoCivil: "solteiro" | "casado" | "divorciado";
  idade: 18 | 25 | 30;
};
```

- `Pessoa`: Objeto com propriedades que têm valores literais específicos.

### **Utilização em Objetos**

```typescript
let pessoa1: Pessoa = {
  sexo: "masculino",
  estadoCivil: "solteiro",
  idade: 25,
};

let pessoa2: Pessoa = {
  sexo: "feminino",
  estadoCivil: "casado",
  idade: 30,
};
```

- Ao criar objetos do tipo `Pessoa`, as propriedades só podem ter os valores literais definidos.

## **Combinação com Outros Tipos**

```typescript
type Coordenada = {
  x: 1 | 2 | 3;
  y: 10 | 20 | 30;
};
```

- `Coordenada`: Objeto com propriedades que têm valores literais específicos para coordenadas.

## **Exemplo**

```typescript
type Resposta = {
  sucesso: true;
  mensagem: string;
} | {
  sucesso: false;
  erro: string;
};

function processarResposta(resposta: Resposta): void {
  if (resposta.sucesso) {
    console.log(`Sucesso: ${resposta.mensagem}`);
  } else {
    console.error(`Erro: ${resposta.erro}`);
  }
}
```

- `Resposta`: Objeto com propriedades literais `sucesso` e `erro`.

## **Benefícios dos Tipos Literais em Objetos**

- **Precisão:** Restringe os valores possíveis para propriedades do objeto.
- **Legibilidade:** Torna claro quais valores são permitidos em cada propriedade.
- **Segurança:** Ajuda a evitar erros de atribuição de valores incorretos.

Os tipos literais em objetos são fundamentais para criar estruturas de dados mais expressivas e seguras no TypeScript. Eles garantem que a forma e os valores dos objetos estejam alinhados com as expectativas do desenvolvedor, proporcionando um código mais robusto e autoexplicativo.