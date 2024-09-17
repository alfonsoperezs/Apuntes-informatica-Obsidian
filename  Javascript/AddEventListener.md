La función `addEventListener` en JavaScript se utiliza para añadir un "escuchador" de eventos a un elemento HTML. Esto permite ejecutar una función específica cuando ocurre un evento determinado (como un clic, pase de ratón, tecla presionada, etc.) en ese elemento.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Ejemplo de addEventListener</title>
</head>
<body>
    <h1 id="encabezado">¡Hola, Mundo!</h1>
    <button id="boton">Haz clic aquí</button>

    <script>
        // Seleccionar el botón y el encabezado por sus IDs
        var boton = document.getElementById("boton");
        var encabezado = document.getElementById("encabezado");

        // Añadir un escuchador de eventos para el clic en el botón
        boton.addEventListener("click", function() {
            // Cambiar el contenido de texto del encabezado
            encabezado.textContent = "¡El texto ha cambiado!";
        });
    </script>
</body>
</html>
```
