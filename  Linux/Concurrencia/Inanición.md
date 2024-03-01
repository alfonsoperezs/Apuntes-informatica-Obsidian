Un proceso puede estar esperando acceso a un recurso compartido sin conseguirlo. Esta situación se denomina inanición. Por ejemplo, si requerimos la reserva de todos los recursos simultáneamente, los procesos que requieran una gran cantidad de recursos pueden quedar en este estado si hay muchos procesos que requieren pocos compitiendo por ellos.

## EJEMPLO

```c
mutex *m1, *m2, *m3; int v1, v2, v3;

void *bloqueo_mucho(void *arg) {
	while(1) {
		lock(m1);
		if (try_lock(m2)) { //Para evitar mantener recursos
			if(try_lock(m3)) { //Para evitar mantener recursos
			// Hacer algo con v1, v2, v3
			}
			unlock(m2);
		}
		unlock(m1);
	}
}
```