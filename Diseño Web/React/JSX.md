Extensión para poder definir nuestros elementos de manera declarativa.

Dado el siguiente código.
```js
const button = h('button', { "data-id": 123 }, 'Button 1');
const button2 = h('button', { "data-id": 456 }, 'Button 2');
const button3 = h('button', { "data-id": 789 }, 'Button 3');

const app = h(React.Fragment, null, [button, button2, button3]);
```

Podemos expresarlo en JSX de esta manera.
```js
<React.Fragment>
  <button data-id="123">Button 1</button>
  <button data-id="456">Button 2</button>
  <button data-id="789">Button 3</button>
</React.Fragment>
```

Los ficheros que utilicen JSX llevarán la extensión `.jsx`

### Expresiones
Se pueden añadir expresiones poniendo la constante entre llaves.
```js
const name = "David"
<h1>Hola, {name}</h1>
```

### CamelCase
Dado que React es Javascript y no HTML, escribiriamos `tabIndex` en lugar de `tab-index`.