Un mutex, abreviatura de "mutual exclusion", es un tipo de mecanismo de sincronización utilizado en programación concurrente para evitar que múltiples procesos o hilos accedan simultáneamente a un recurso compartido, como una sección crítica de código o un recurso en memoria.

La librería pthread implementa mutex:

```c
pthread_mutex_t *mutex;

int pthread_mutex_init(pthread_mutex_t *, pthread_mutex_attr *); // inicializa el mutex
int pthread_mutex_destroy(pthread_mutex_t *); // destruye el mutex

int pthread_mutex_lock(pthread_mutex_t *); // bloquea el mutex
int pthread_mutex_trylock(pthread_mutex_t *); // intenta bloquear el mutex
int pthread_mutex_unlock(pthread_mutex_t *); // desbloquea el mutex
```



