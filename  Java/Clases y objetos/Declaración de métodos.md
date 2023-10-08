La declaración de métodos en Java es esencial para definir el comportamiento y la funcionalidad de una clase. A continuación, se describen los aspectos clave relacionados con la declaración de métodos:

**Especificadores de Acceso:**
Los especificadores de acceso para métodos son los mismos que para atributos:

- `public`: Los métodos públicos son visibles para todas las clases y pueden ser accedidos desde cualquier lugar.
- `protected`: Los métodos protegidos son visibles para las subclases de la clase original y también para las clases en el mismo paquete que la clase original.
- (Sin especificador): Si no se especifica ningún especificador de acceso, el método es visible solo para las clases en el mismo paquete que la clase original.
- `private`: Los métodos privados son visibles solo dentro de la propia clase y no pueden ser accedidos desde fuera de la clase.

**Modificadores:**
Los modificadores pueden aplicarse a métodos:

- `static`: Los métodos estáticos pertenecen a la clase en lugar de a una instancia particular. Se pueden llamar sin crear una instancia de la clase.
- `abstract`: Los métodos abstractos son métodos que no están definidos en la clase actual y están destinados a ser implementados por subclases.
- `final`: Los métodos finales evitan que sean sobrescritos por subclases. Si una clase es final, todos sus métodos son implícitamente finales.
- `native`: Los métodos nativos están escritos en otro lenguaje (como C o C++) y se utilizan para interactuar con código de nivel inferior.
- `synchronized`: Los métodos sincronizados se utilizan en la programación multihilo para asegurarse de que solo un hilo pueda ejecutar el método a la vez.

**Paso de Parámetros:**
En Java, todos los parámetros se pasan por valor:

- Para tipos básicos (int, float, etc.), los parámetros actuales se copian en los parámetros formales del método.
- Para objetos, se pasa el valor de su puntero por valor, lo que significa que se pasa una referencia al objeto.

**Tipos de Retorno:**
Los métodos de Java devuelven un tipo de retorno que puede ser: un objeto, un tipo básico o un valor void (que significa que el método no devuelve nada). 

Para devolver un valor dentro del método se usa la palabra clave `return`. [1]

Los métodos sólo pueden devolver un elemento. Para devolver varios elementos lo habitual es agruparlos en un objeto.

[1] [[return]]