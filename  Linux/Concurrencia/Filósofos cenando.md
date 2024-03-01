El problema de los filósofos cenando es un clásico en la teoría de la concurrencia. Imaginemos N filósofos sentados alrededor de una mesa circular, cada uno necesita dos cubiertos para comer, compartiendo uno con cada vecino. El desafío es diseñar una solución que evite la inanición de cualquier filósofo al mismo tiempo que se garantiza el acceso a los cubiertos compartidos.

![[Captura de pantalla (77).png]]

## Un mutex por tenedor

Un mutex por tenedor (comen de uno en uno)

```c
#define N 
#define LFORK(I) (((I) + 1) % N)
#define RFORK(I) (I)
#define min(x,y) ((x) < (y)? (x):(y))
#define max(x,y) ((x) > (y)? (x):(y))

mutex_t fork[n];

void philosofer(int i){
	while(1){
		pick_up(i); // seccion crítica 1
		eat();
		put_down(i); // seccion critica 2
		thinking();
	}
}

void pick_up(int i){
	int left = lfork(i);
	int right = rfork(i);
	
	lock(fork[right]);
	lock(fork[left]); // al haber 2 lock, se puede dar interbloqueo
}

void pick_up(int i){
	int left = lfork(i);
	int right = rfork(i);
	
	lock(fork[min(left,right)]);
	lock(fork[max(left,right)]); // al haber 2 lock, se puede dar interbloqueo
}

void put_down(int i){
	int left = lfork(i);
	int right = rfork(i);
	
	unlock(fork[left]);
	unlock(fork[right]);	
}
```

- Se puede dar que todos los filósofos cojan el tenedor de la izquierda, y al intentar coger el de la derecha, se produzca interbloqueo. Toda la mesa se ve implicada por dependencias


Un mutex por tenedor, pero solucionando el interbloqueo, ya que se evita el Hold & Wait (comen varios)

```c
#define N 
#define LFORK(I) (((I) + 1) % N)
#define RFORK(I) (I)
#define min(x,y) ((x) < (y)? (x):(y))
#define max(x,y) ((x) > (y)? (x):(y))

mutex_t fork[n];

void philosofer(int i){
	while(1){
		pick_up(i); // seccion crítica 1
		eat();
		put_down(i); // seccion critica 2
		thinking();
	}
}

void pick_up(int i){
	int left = lfork(i);
	int right = rfork(i);
	
	while(1){
		lock(fork[right]);
		if(trylock(fork[left]) == 0)
			break
		unlock(fork[right]);
		usleep(rand % 10);
	}
}

void put_down(int i){
	int left = lfork(i);
	int right = rfork(i);
	
	unlock(fork[left]);
	unlock(fork[right]);	
}
```

- Se produce inanición
- Hay tiempo de espera

## Un mutex para toda la mesa

Un mutex para la mesa y una condición por filósofo.

```
#define N
#define THINKING 0
#define EATING 1
#define LPHIL(I) (((I) + 1) % N)
#define RPHIL(I) (((I) - 1) % N)

cond_t NO_FORKS

mutex_t m;
int phil[N];

void pick_up(int i){
	int left = lphil(i);
	int right = rphil(i);
	
	lock(m);
	phil[i] = hungry;
	while(phil[right] == EATING || phil[right] == EATING){
		wait(NO_FORKS);
	}
	phil[i] = EATING;
	unlock(m);	
}

void put_down(int i){
	int left = lphil(i);
	int right = rphil(i);
	
	lock(m);
	phil[i] = THINKING;
	// broadcast(NO_FORKS);
	if(phil[left] == hungry)
		signal(no_forks[left]);
	if(phil[right] == hungry)
		signal(no_forks[right]);
	unlock(m);
}
```

- Sigue pudiendo haber inanición.
- Menor concurrencia

Un mutex para la mesa, una condición por filósofo y limitación de espera.

```
#define N
#define THINKING 0
#define EATING 1
#define LPHIL(I) (((I) + 1) % N)
#define RPHIL(I) (((I) - 1) % N)
#define HUNGRY 2

cond_t NO_FORKS
time_t wait_time[n]

mutex_t m;
int phil[N];

void pick_up(int i){
	int left = lphil(i);
	int right = rphil(i);
	
	lock(m);
	phil[i] = hungry;
	wait_time[i] = time(null);
	while(phil[right] == EATING || phil[right] == EATING){
		wait(NO_FORKS);
	}
	phil[i] = EATING;
	unlock(m);	
}

void put_down(int i){
	int left = lphil(i);
	int right = rphil(i);
	
	lock(m);
	phil[i] = THINKING;
	// broadcast(NO_FORKS);
	if(phil[left] == hungry)
		signal(no_forks[left]);
	if(phil[right] == hungry)
		signal(no_forks[right]);
	unlock(m);
}

int can_i_eat(i){
	if(phil[left] == EATING || phil[right] == eating)
		return 0;
	if(time(null) - time_wait[i] > max_wait)
		return 1;
	if(time(null) - time_wait[left] > max_wait || time(null) - time_wait[right] > max_wait)
		return 0;
	return 1;
}
```

- Menor concurrencia