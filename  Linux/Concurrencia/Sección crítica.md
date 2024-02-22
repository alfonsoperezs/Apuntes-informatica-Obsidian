La sección crítica es la parte de código que accede a un recurso compartido con otro `proceso/thread`.

## EJEMPLO:

```
int i=0; // Variable global, compartida entre threads 

void *incrementar(void *arg) { 
	int v; // Variable local, una por thread 
	// inicio sección crítica
	v=i; 
	v++; 
	i=v; 
	// fin sección crítica
} 
void lanzar_thread() { 
	pthread_t thr; 
	pthread_create(&thr, NULL, incrementar, NULL); 
}
```

La sección crítica es la parte de código donde estamos tocando recursos compartidos, en este caso la variable i.

## Problemas en la sección crítica

Nos podemos encontrar la situación de que mas de un thread acceda a la vez a la sección crítica dándose diversas situaciones:
	- Que un thread vaya mas rápido que otro y primero acceda a la sección crítica uno de ellos y a continuación el otro, no alterando la ejecución del programa.
	- Que los dos threads accedan a la vez y hagan las operaciones dejando totalmente impredecible el comportamiento de la ejecución del programa.


