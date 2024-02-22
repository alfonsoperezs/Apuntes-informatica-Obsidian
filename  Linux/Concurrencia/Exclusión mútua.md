Consiste en garantizar que dos procesos no pueden estar en su sección crítica simultáneamente.

## EJEMPLO

Vamos a añadir un mecanismo que solo permita un thread a la vez en la sección crítica:

```
void *incrementar(void *arg) {
	int v;
	lock;
	v = i;
	v++;
	i=v;
	unlock;
}
```

El primer thread que llegue a lock bloquea el acceso a los demás. Cuando ese proceso haga unlock se permite el paso al siguiente. Este mecanismo de bloqueo se denomina [[Mútex]].