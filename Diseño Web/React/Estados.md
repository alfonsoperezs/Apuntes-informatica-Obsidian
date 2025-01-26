Estructura de datos que guarda los valores que pueden cambiar durante la vida de un componente. Cada vez que el estado de un componente cambia, React vuelve a renderizar ese componente para reflejar los cambios.
## Renderizado condicional
Renderiza una cosa u otra dependiendo de una condición. Con esto logramos que React sea dinámico.
```js
const text = isFollowing ? 'Siguiendo' : 'Seguir'
const btClassName = isFollowing ? 'card is-following' : 'card'
```
## useState
Es un Hook de React que te permite agregar una variable de estado a tu componente.
```js
import {useState} from 'react'
```

Vamos a crear nuestro primer estado.
```js
const [isFollowing, setIsFollowing] = useState(false)
```

`useState` devuelve un array de dos posiciones. En la primera posición tendremos el valor del estado y en la segunda posición una función que nos permitirá actualizar el estado.

> [!important]
> Si utilizamos una propiedad para inicializar un componente, solo se inicializa una vez, no cada vez que la propiedad cambia.
### Cambio de estado
```js
const handleClick = () => {
	setIsFollowing(!isFollowing)
}

<button onClick={handleClick}>Follow</button>
```

Si tuvieramos varios componentes iguales, cada estado sería independiente, dado que es un estado interno.

> [!note]
>  Una re-renderización de un componente padre provoca que se re-rendericen los componentes hijos, necesiten o no actualizarse.

