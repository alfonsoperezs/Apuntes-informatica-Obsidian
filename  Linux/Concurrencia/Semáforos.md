Los semáforos son un mecanismo de control de acceso a secciones críticas en programación concurrente. Cada semáforo tiene un valor numérico asociado que se establece al crearlo. Cuando un proceso intenta bloquear (o decrementar) un semáforo, su valor se reduce; y cuando se libera (o incrementa) un semáforo, su valor aumenta. Cuando el valor de un semáforo alcanza 0, el proceso que intenta bloquearlo se queda en espera o bloqueado hasta que el semáforo se libere por otro proceso.

## P(bloquear) y V(liberar)

```c
V(semaphore S) {
	S=S+1;
}
P(semaphore S) {
	while(1) {
		if(S > 0) { S=S-1; break; }
	}
}
```

Un [[Mútex]] es un caso especial de semáforo con valor 1.

## Semáforos Posix 

```c
sem_t *sem;

int sem_init(sem_t *sem, int pshared, unsigned int value);
int sem_destroy(sem_t *sem);

int sem_wait(sem_t *sem); // P
int sem_trywait(sem_t *sem);
int sem_timedwait(sem_t *sem, const struct timespec *abs_timeoout);
int sem_post(sem_t *sem); // V
```

La estructura sem tiene que estar en memoria compartida entre los procesos.