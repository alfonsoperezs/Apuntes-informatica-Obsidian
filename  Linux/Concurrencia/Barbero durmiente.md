Este escenario hipotético presenta un único barbero que atiende a los clientes en una barbería. Después de atender a un cliente, el barbero verifica si hay más clientes esperando en la sala de espera. Si hay alguno, lo atiende inmediatamente; de lo contrario, se retira a descansar. Cuando un nuevo cliente llega a la barbería, este verifica si el barbero está libre; si no lo está, se une a los clientes en la sala de espera. Sin embargo, si la sala de espera está llena, el nuevo cliente se va, sin poder ser atendido.

![[Captura de pantalla (78).png]]

## Con un solo barbero

Puede surgir que un cliente llega al mismo tiempo que el barbero termina: mientras el cliente va a la sala de espera, el barbero la comprueba y la ve vacía: los dos esperan indefinidamente. Por tanto hay que sincronizar barbero y cliente:

```c
// BARBERO
while(1) {
	pthread_mutex_lock(&mutex);
	if (!customers_waiting) {
		barber_state = SLEEPING;
		pthread_cond_wait(&no_customers, &mutex);
	}
	else {
		pthread_cond_signal(&waiting_room);
		waiting_customers--;
	}
	pthread_mutex_unlock(&mutex);
	cut_hair();
}
```

```c
// CLIENTE
pthread_mutex_lock(&mutex);
if(waiting_customers == MAX_CUSTOMERS)
	pthread_mutex_unlock(&mutex);
else {
	if(barber_state==SLEEPING) {
		pthread_cond_signal(&no_customers);
		barber_state=WORKING;
	} else {
		waiting_customers++;
		pthread_cond_wait(&waiting_room, &mutex);
	}
	pthread_mutex_unlock(&mutex);
	get_hair_cut();
}
```

## Con múltiples barberos

Necesitamos seguir dos estrategias:
- Añadir un contador de barberos libres en vez del estado. Los barberos incrementan el contador al irse a dormir, y los clientes lo decrementan a despertar un barbero.
- Guardar el estado de cada barbero. Los barberos ponen su estado a SLEEPING, y los clientes buscan un barbero que esté SLEEPING y lo ponen a WORKING. Hace falta una condición para dormir a cada barbero.

```c
// BARBERO
while(1) {
	pthread_mutex_lock(&mutex);
	if (!waiting_customers) {
		barberos_libres++;
		pthread_cond_wait(&no_customers, &mutex);
	} else {
		pthread_cond_signal(&waiting_room);
		waiting_customers--;
	}
	pthread_mutex_unlock(&mutex);
	cut_hair();
}
```

```c
// CLIENTE
pthread_mutex_lock(&mutex);
if(waiting_customers == MAX_CUSTOMERS)
	pthread_mutex_unlock(&mutex);
else {
	if(barberos_libres>0) {
		pthread_cond_signal(&no_customers);
		barberos_libres--;
	} else {
		waiting_customers++;
		pthread_cond_wait(&waiting_room, &mutex);
	}
	pthread_mutex_unlock(&mutex);
	get_hair_cut();
}
```

## Solución con semáforos

Necesitamos dos semáforos:
- Uno con la cuenta de clientes esperando.
- Otro con el número de barberos libres.

```c
sem_t customers;
sem_t barber;
sem_t free_seats;

int free_seats = N;

sem_init(&customers, 1, 0);
sem_init(&barber, 1, 0);
sem_init(&free_seats, 1, 1);
```

```c
// BARBERO
while(1) {
	sem_wait(&customers); // Esperar por clientes
	sem_wait(&free_seats); // bloquear contador
	free_seats++;
	sem_post(&barber); // Despertar un cliente
	sem_post(&free_seats); // desbloquear contador
	cut_hair();
}
```

```c
// CLIENTE
sem_wait(&free_seats); // bloquear contador
if(free_seats>0) {
	free_seats--; // marcar silla ocupada
	sem_post(&customer); // Incrementar clientes
	sem_post(&free_seats); // soltar contador
	sem_wait(&barber); // Esperar por un barbero libre
	get_hair_cut();
} else sem_post(&free_seats);
```