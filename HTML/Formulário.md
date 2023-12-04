# Formulários em HTML

Os formulários em HTML são elementos fundamentais para a coleta de informações dos usuários. Eles permitem a interação do usuário com a página da web, como o envio de dados e o fornecimento de feedback. 

## Estrutura Básica de um Formulário

```html
<form action="processar.php" method="POST">
    <!-- Campos de entrada, rótulos e outros elementos do formulário -->
    <label for="nome">Nome:</label>
    <input type="text" id="nome" name="nome" required>

    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>

    <input type="submit" value="Enviar">
</form>
```

- `<form>`: Define um formulário.
- `action`: Define o URL para onde os dados do formulário serão enviados.
- `method`: Define o método HTTP para enviar os dados (GET ou POST).

## Tipos de Campos de Entrada

### Campo de Texto (`<input type="text">`)

```html
<input type="text" id="nome" name="nome" required>
```

### Campo de Email (`<input type="email">`)

```html
<input type="email" id="email" name="email" required>
```

### Campo de Senha (`<input type="password">`)

```html
<input type="password" id="senha" name="senha" required>
```

### Campo de Texto Multilinha (`<textarea>`)

```html
<textarea id="comentario" name="comentario" rows="4" cols="50"></textarea>
```

## Tipos de Campos de Seleção

### Caixa de Seleção (`<input type="checkbox">`)

```html
<input type="checkbox" id="sabor1" name="sabores" value="baunilha">
<input type="checkbox" id="sabor2" name="sabores" value="chocolate">
```

### Botões de Opção (`<input type="radio">`)

```html
<input type="radio" id="masculino" name="genero" value="masculino">
<input type="radio" id="feminino" name="genero" value="feminino">
```

### Menu Suspenso (`<select>` e `<option>`)

```html
<select id="pais" name="pais">
    <option value="brasil">Brasil</option>
    <option value="eua">Estados Unidos</option>
    <option value="canada">Canadá</option>
</select>
```

## Outros Elementos

### Botão de Envio (`<input type="submit">`)

```html
<input type="submit" value="Enviar">
```

### Botão de Reset (`<input type="reset">`)

```html
<input type="reset" value="Limpar">
```

### Campos Ocultos (`<input type="hidden">`)

```html
<input type="hidden" id="id_usuario" name="id_usuario" value="123">
```

## Atributos Importantes

### `id` e `name`

- `id`: Define um identificador exclusivo para um elemento.
- `name`: Define o nome do campo que será enviado com os dados do formulário.

### `required`

- Torna um campo obrigatório para preenchimento.

### `for` (rótulos)

- Associa um rótulo a um campo de entrada usando o `id`.

## Validação e Segurança

- A validação do lado do cliente pode ser feita usando atributos como `required`, `pattern`, `min`, `max`, etc.
- A validação do lado do servidor é essencial para garantir a segurança dos dados.
