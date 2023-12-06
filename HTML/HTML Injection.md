# Cheatsheet sobre Injeção de HTML

A injeção de HTML é uma vulnerabilidade de segurança que ocorre quando dados não confiáveis são inseridos em um contexto HTML sem a devida validação ou sanitização. Esse tipo de ataque pode levar a execução de scripts maliciosos no navegador do usuário e comprometer a segurança da aplicação. Aqui está um guia para entender, identificar e prevenir a injeção de HTML.

## Formas Comuns de Injeção de HTML:

### 1. **Inclusão de Tags HTML:**
```html
<!-- Dados não sanitizados -->
<p>{{dados_inseguros}}</p>
```

### 2. **Atributos de Eventos:**
```html
<!-- Dados não sanitizados -->
<button onclick="{{codigo_malicioso}}">Clique Aqui</button>
```

### 3. **Scripts Embutidos:**
```html
<!-- Dados não sanitizados -->
<script>{{script_malicioso}}</script>
```

Estas tags podem, por exemplo, serem inseridas em formulários não sanitizados ou em dados contidos no conteúdo ou header das requisições HTTP. 

## Riscos Associados:

1. **Execução de Scripts Maliciosos:** A injeção de HTML pode permitir a execução de scripts maliciosos no contexto do usuário, comprometendo a segurança.

2. **Roubo de Cookies e Sessões:** Atacantes podem utilizar a injeção para roubar informações sensíveis, como cookies de autenticação.

3. **Redirecionamento de Página:** Os atacantes podem redirecionar usuários para páginas maliciosas.

## Como Prevenir a Injeção de HTML:

### 1. **Sanitização de Dados:**
- Utilize bibliotecas ou frameworks que ofereçam funções de sanitização de HTML para remover ou neutralizar tags e scripts maliciosos.

### 2. **Utilização de Codificação Adequada:**
- Codifique os dados antes de inseri-los em contexto HTML usando funções como `htmlspecialchars` em PHP ou equivalente em outras linguagens.

### 3. **Princípio do Menor Privilégio:**
- Evite utilizar dados não confiáveis diretamente no HTML sempre que possível. Utilize uma abordagem de "menor privilégio" para limitar o acesso a dados sensíveis.

### 4. **Validação do Lado do Servidor:**
- Valide e sanitize os dados no lado do servidor antes de enviá-los para o cliente.

### 5. **Utilização de Content Security Policy (CSP):**
- Implemente políticas de segurança de conteúdo para restringir o tipo de conteúdo executado em uma página, reduzindo assim os riscos de execução de scripts maliciosos.

### 6. **Treinamento de Desenvolvedores:**
- Eduque a equipe de desenvolvimento sobre práticas seguras de codificação para evitar vulnerabilidades desde o início do desenvolvimento.

### 7. **Monitoramento e Auditoria de Código:**
- Realize auditorias de código regulares e implemente sistemas de monitoramento para identificar possíveis vulnerabilidades.

A injeção de HTML é uma ameaça séria à segurança da aplicação, mas com práticas adequadas de codificação e implementação de medidas preventivas, é possível reduzir significativamente os riscos associados a esse tipo de ataque.