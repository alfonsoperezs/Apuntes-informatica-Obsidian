Un componente es una función que devuelve un elemento.

```js
const Button = ({text}) => {
	return(
		<button>{text}</button>
	)
}

root.render(
	<Button text="Button 1">
)
```

Si un componente no tiene que envolver nada, cerramos con `/`.
```js
root.render(
	<Button />
)
```
### PascalCase
Si no utilizamos PascalCase, es decir `Button` en lugar de `button`, no aparecería el componente. React no es capaz de diferenciar si escribiste un componente o un elemento HTML.

## Reutilización de componentes
La base para reutilizar algo es poder parametrizarlo.

```js
export function followCard({userName, name, isFollowing}){
	return(...)
}
```
Las propiedades deben ser inmutables. Es mala práctica modificarlos.
### Links
Esto no funcionaría.
```js
src="https://hola.com/{userName}"
```

#### Opción 1
```js
const imSrc = `https://hola.com/${userName}`

src={imSrc}
```
#### Opción 2
```js
src={`https://hola.com/${userName}`}
```

### Paso de funciones
Es posible pasar por parámetro funciones.
```js
const f = {user} => `@${user}`

<Comp format={f}>
```

### Paso de elementos
Es posible pasar elementos por parámetro.
```js
const f = (<span>@{user}</span>)
```

### Propiedad Children
```html
<button>
	Like // <- Esto seria children
</button>
```

```js
export function followCard({children, userName, name, isFollowing}){}

<FollowCard>David</FollowCard> // David sería la propiedad children
```

### Paso de objetos como propiedad
>[!warning]
> Suele ser mala práctica hacerlo

```js
const hola = {name: 'David', userName 'davidd'}
<Comp {... hola}>
```