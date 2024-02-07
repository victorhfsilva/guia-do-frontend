# Testes de Interações do Usuário com o React Testing Library

## 1. Cliques

Simule cliques em elementos como botões, links e outros elementos clicáveis.

```javascript
fireEvent.click(elemento);
```

## 2. Digitação

Simule a digitação de texto em elementos de entrada de texto.

```javascript
fireEvent.change(inputElemento, { target: { value: 'Texto digitado' }});
```

## 3. Foco

Simule a focalização em elementos como campos de entrada de texto.

```javascript
fireEvent.focus(inputElemento);
```

## 4. Desfoco

Simule o desfoque de elementos, como sair de campos de entrada de texto.

```javascript
fireEvent.blur(inputElemento);
```

## 5. Envio de formulário

Simule o envio de formulários para testar a submissão de dados.

```javascript
fireEvent.submit(formElemento);
```

## 6. Teclas

Simule a pressão de teclas em elementos para testar atalhos de teclado ou ações específicas.

```javascript
fireEvent.keyDown(elemento, { key: 'Enter', keyCode: 13 });
```

## 7. Arrastar e Soltar

Simule eventos de arrastar e soltar para testar funcionalidades de arrastar e soltar.

```javascript
const draggableElement = screen.getByTestId('draggable');
const droppableElement = screen.getByTestId('droppable');
fireEvent.dragStart(draggableElement);
fireEvent.drop(droppableElement);
```

## 8. Passar o Mouse

Simule eventos de passar o mouse sobre elementos para testar efeitos de hover.

```javascript
fireEvent.mouseEnter(elemento);
```

## 9. Rolagem

Simule eventos de rolagem em elementos para testar a rolagem dentro de contêineres.

```javascript
fireEvent.scroll(elemento, { target: { scrollLeft: 100 } });
```