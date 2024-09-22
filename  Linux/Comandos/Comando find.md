Busca archivos y directorios dentro de una jerarquía de directorios, basándose en una variedad de criterios como nombre, tipo, tamaño, fecha de modificación, entre otros.

```bash
find [ruta] [condiciones]
```

# Ejemplo
---

Queremos buscar el fichero `sources.list`. Sabemos que se ubica en /etc. Por tanto, haríamos:

```bash
find /etc -name "sources.list"
```

