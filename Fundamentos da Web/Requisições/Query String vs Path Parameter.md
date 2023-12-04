# Query String vs Path Parameter

## **Query String**

- **Formato**: Normalmente anexada à URL após o caractere "?", consiste em pares de chave e valor separados por "&".
- **Exemplo**: `?chave1=valor1&chave2=valor2`
- **Quando Usar**:
    1. **Filtros ou Opções de Consulta**: Use Query Strings quando precisar fornecer opções de consulta ou filtros para recuperar dados de um recurso. Por exemplo, ao filtrar produtos por categoria ou ordená-los por preço.
    2. **Parâmetros Opcionais**: São ideais para parâmetros opcionais, onde você pode ter uma variedade de combinações.
    3. **Parâmetros de Busca**: Quando os parâmetros são usados para pesquisa em uma lista de recursos.

## **Path Parameter (ou Route Parameter)**

- **Formato**: Faz parte da própria URL e é geralmente definido dentro de chaves "{}".
- **Exemplo**: `/recurso/{id}`
- **Quando Usar**:
    1. **Identificação de Recursos Únicos**: Use Path Parameters quando estiver identificando um recurso único em uma URL, como um ID de usuário, ID de postagem, etc.
    2. **Roteamento Dinâmico**: Útil para criar rotas dinâmicas em aplicativos da web ou API RESTful, onde o caminho é variável.

## **Diferenças Principais**

1. **Natureza da Informação**: Query Strings são usadas para fornecer informações opcionais ou parâmetros de consulta, enquanto Path Parameters são usados para identificar recursos específicos.

2. **Visibilidade**: Query Strings são mais visíveis e podem ser alteradas facilmente na barra de endereços do navegador. Path Parameters são incorporados na própria URL.

3. **Recomendações Gerais**:
   - Use Query Strings para filtrar, ordenar ou fornecer opções de consulta em listas de recursos.
   - Use Path Parameters para identificar recursos únicos ou para criar rotas dinâmicas.

## **Exemplos de Uso Comum**:

- **Query String**: `/produtos?categoria=eletrônicos&ordenar=preco`
- **Path Parameter**: `/usuarios/{id}`

Lembre-se de que a escolha entre Query Strings e Path Parameters depende do contexto e dos requisitos específicos do seu aplicativo ou serviço. Ambos têm seu lugar e podem ser usados em conjunto para criar URLs expressivas e eficazes.
