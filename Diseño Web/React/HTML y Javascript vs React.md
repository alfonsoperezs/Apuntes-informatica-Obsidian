## Ejemplo en HTML y Javascript
Si queremos crear un botón (supongamos un botón de dar like a una publicación).
```html
<button data-id="123">like</button>
```

Quiero que al hacer click de like a la publicación.
```js
// recuperamos el boton
const button = document.querySelector('button')
// al hacer click, ejecutamos una función
button.addEventListener('click', function(){
	const id = this.getAttribute('data-id')
	// llamamos servicio para actualizar
	// toggleLike(id)
	if (button.classList.contains('liked')) {
	    button.classList.remove('liked')
	    button.innerText = 'Me gusta'
	} else {
	    button.classList.add('liked')
	    button.innerText = 'Quitar me gusta'
	}
})
```

### Problemas
- El código es imperativo, es decir, le estamos diciendo en todo momento cómo tiene que actuar. No es escalable.
- El código es difícil de reutilizar. Si quisiesemos duplicar los botones, no funcionarían a menos que ajustásemos el código.
- Mismos elementos pertenecientes a funcionalidades sin relación tienen la lógica en el mismo fragmento del código

## Ejemplo en React
Creamos un div donde queremos renderizar nuestra aplicación.
```html
<div id="app"></div>
```

Y nuestro código React.
```js
import React from "https://esm.sh/react@18.2.0"
import ReactDOM from "https://esm.sh/react-dom@18.2.0/client";

// recuperamos el elemento donde queremos inyectar react
const appDomElement = document.getElementById('app');
// creamos arbol de componentes y le indicamos donde lo creamos
const root = ReactDOM.createRoot(appDomElement);
// creamos el botón
const button = React.createElement('button', {"data-id": 123}, 'me gusta')
// (elemento, propiedades, children)
// le decimos que queremos renderizar (el botón)
root.render(button)

```

>[!Important]
>En react no se pueden insertar directamente HTML. Es una medida de seguridad para que alguien no pueda insertar código (existe una manera de saltarsela)

```js
root.render('<button>like</button>') // muestra por pantalla texto y no un botón
```
### Ventajas de React
- Podemos utilizar código React para inyectarlo en cualquier componente de cualquier página web.

### Renderizar más de un elemento a la vez
No podemos renderizar más de un elemento a la vez.
```js
root.render(button1, button2, button3) // no funciona
```

#### Solución 1
Meterlo en un div.
```js
const div = React.createElement('div', null, [but1, but2, but3])
```

Problema: Puedo no querer un div.

#### Solución 2
Envolver elementos en elemento vacío (React.Fragment)
```js
const div = React.createElement(React.Fragment, null, [but1, but2, but3])
```