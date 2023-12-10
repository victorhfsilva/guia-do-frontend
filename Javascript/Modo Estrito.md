# **Modo Estrito em JavaScript**

O "modo estrito" é uma funcionalidade do JavaScript que introduz verificações e regras mais rigorosas para ajudar a evitar erros comuns e problemas em seu código. 

## **Ativar o Modo Estrito:**
   Para ativar o modo estrito, você deve incluir a seguinte linha no topo de seu arquivo JavaScript:

   ```javascript
   "use strict";
   ```

   ou você pode ativar o modo estrito em uma função específica:

   ```javascript
   function minhaFuncao() {
     "use strict";
     // Código no modo estrito
   }
   ```

## **Regras do Modo Estrito:**

   - Variáveis não declaradas não são permitidas. Isso evita vazamentos globais.

   - Atribuir valor a variáveis não graváveis (como objetos e funções) lança erros.

   - Omissão do uso da palavra-chave `var` ao declarar variáveis lança um erro.

   - "delete" não pode ser usado em variáveis, funções ou funções de parâmetro.

   - Parâmetros duplicados em funções lançam erros.

   - "this" não vincula ao objeto global em funções não estritas.

   - Palavras-chave reservadas, como `eval` e `arguments`, não podem ser usadas como identificadores.

## **Benefícios do Modo Estrito:**

   - Ajuda a evitar erros silenciosos e comportamentos não esperados.

   - Torna o código mais seguro e previsível.

   - Facilita a otimização do código pelo mecanismo JavaScript.

## **Compatibilidade:**

   - O modo estrito é amplamente suportado em navegadores modernos.

   - É seguro usar o modo estrito na maioria dos projetos.

   - Certifique-se de testar e verificar a compatibilidade em navegadores mais antigos, se necessário.

## **Exemplo de Uso:**

   ```javascript
   "use strict";

   function calcularValor() {
     total = 100; // Isso lançará um erro no modo estrito, pois 'total' não foi declarado.
     return total;
   }
   ```

## Mais Informações

- [Strict Mode: Mdn Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Strict_mode)


Lembrando que é uma boa prática usar o modo estrito para evitar problemas em seu código JavaScript. Ele ajuda a tornar seu código mais robusto e evita comportamentos inesperados.