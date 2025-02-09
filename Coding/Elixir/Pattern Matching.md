## El operador =
En Elixir, el operador `=` no es una asignación tradicional, sino un operador de coincidencia. En lugar de asignar un valor a una variable, Elixir intenta hacer coincidir la estructura del lado derecho con el patrón del lado izquierdo.
### Ejemplo
```erlang
x = 10
# x ahora vale 10

{a, b} = {1, 2}
# a = 1, b = 2

[a, b, c] = [3, 4, 5]
# a = 3, b = 4, c = 5
```

## Pattern Matching en funciones
Se pueden definir múltiples versiones de una misma función, y Elixir ejecutará la que coincida con los parámetros dados.
### Ejemplo
```erlang
defmodule Ejemplo do
  def saludar("Carlos"), do: "Hola, Carlos!"
  def saludar(_nombre), do: "Hola, desconocido!"
end

Ejemplo.saludar("Carlos") # "Hola, Carlos!"
Ejemplo.saludar("Ana")    # "Hola, desconocido!"
```

## Guard Clauses
Las guard clauses permiten agregar condiciones en la coincidencia.

>[!important]
> Deben ser expresiones rápidas de evaluar

### Ejemplo
```erlang
def mayor_de_edad?(edad) when edad >= 18, do: true
def mayor_de_edad?(_edad), do: false

mayor_de_edad?(20) # true
mayor_de_edad?(15) # false
```