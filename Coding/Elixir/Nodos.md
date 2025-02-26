Un nodo es una máquina virtual de elixir. En un mismo pc puede haber varios nodos.
Para lanzar un nodo basta con lanzar la máquina con un nombre.

```bash
iex --sname borg
```

Los procesos pueden comunicarse entre nodos, por ejemplo, usando `ping`. No es necesario que un nodo se comunique con todos para ser conocido, bastaría con uno.

### Tipos de nombres de nodos
- Cortos: Usados solo en la red local.
- Largos: Usados en cualquier tipo de red, y no van cifrados.

> [!warning]
> No deben mezclarse los nombres cortos y largos

### Cookies
Cada nodo tiene una cookie, que se genera aleatoriamente por defecto y se guarda en un archivo. Para que dos nodos puedan comunicarse, deben tener la misma cookie, de lo contrario, se genera un error.

### trap()
En Elixir, `trap` es una función que te permite interceptar señales de salida de un proceso. Esto es útil para manejar escenarios donde un proceso hijo termina de forma inesperada o envía una señal de salida específica.