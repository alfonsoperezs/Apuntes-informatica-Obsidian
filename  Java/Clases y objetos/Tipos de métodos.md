**Métodos de Clase (Métodos Estáticos):**
- No pertenecen a una instancia específica.
- No pueden acceder a atributos ni métodos de instancia.
- No utilizan el puntero explícito `this`.
- Útiles cuando no se necesita acceder al estado del objeto.
- Se llaman en la clase misma.

**Métodos Constructores:**
- Utilizados para crear e inicializar objetos.
- Deben tener el mismo nombre que la clase.
- No devuelven ningún valor (ni `void`).
- Se llaman usando `new`.
- Pueden acceder al puntero `this`.

**Encadenamiento de Constructores:**
- Se pueden tener varios constructores con diferentes parámetros.
- Comúnmente se llaman entre sí usando `this` para reutilizar lógica de inicialización.

**Métodos Destructores en Java:**
- En Java, no existen métodos destructores.
- Se utiliza la recolección de basura para liberar memoria automáticamente.

**Otros Métodos en Java:**
- **`toString()`:** Devuelve una representación en cadena (`String`) del objeto. Puede ser redefinido para una representación más útil.
- **`main()`:** Punto de entrada para la ejecución de un programa Java. Cualquier clase puede tener un método `main()` para iniciar el programa.

[Enlaces de interés] [[new]] [[this]] 