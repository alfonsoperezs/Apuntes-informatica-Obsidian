Interbloqueo es una situación en que dos o más procesos están esperando por recursos que tiene ocupado el otro.

## EJEMPLO:

Suponemos a un thread que ejecuta el siguiente código:

```
int protected_add(int *v1 (=valor1), mutex *m1(=m_valor1),
int *v2(=valor2), mutex *m2 (=m_valor2)) {
	int x;
	lock(m_valor1);
	lock(m_valor2);
	x=valor1+valor2;
	unlock(m_valor2);
	unlock(m_valor1);
	return x;
}
```

Por otro lado otro thread ejecuta la misma función pero con el orden de las variables cambiado:

```
int protected_add(int *v1 (=valor2), mutex *m1(=m_valor2),
int *v2(=valor1), mutex *m2 (=m_valor1)){
	int x;
	lock(m_valor2);
	lock(m_valor1);
	x=valor2+valor1;
	unlock(m_valor1);
	unlock(m_valor2);
	return x;
}
```

El thread 1 bloquea m_valor1, y thread 2 bloquea m_valor2. Como ambos threads están esperando por el mutex que tiene el otro, se da interbloqueo.

## Condiciones para que se produzca

- Exclusión mutua: existen recursos no compartibles.
- Hold and wait: se permite que un proceso tenga recursos reservados mientras espera para reservar otros.
- No apropiación: El sistema operativo no puede liberar recursos reservados.
- Espera circular: Los procesos esperan por recursos reservados por procesos que esperan por los primeros.

## Prevención

1. Evitar hold and wait haciendo que los procesos reserven todos los recursos necesarios de una vez en vez de mantener reservados unos mientras esperan.

```
int protected_add(int *v1, mutex *m1, int *v2, mutex *m2) {
	int x;
	while(1) {
		lock(m1);
		if(trylock(m2)) { //Si falla libera m1 y reintenta
			unlock(m1);
			continue;
		}
		x=v1+v2;
		unlock(m1);
		unlock(m2);
		break;
	}
	return x;
}
```

2. La espera circular se puede evitar con una reserva ordenada de recursos.

```
int protected_add(int *v1, mutex *m1, int ordenv1, int *v2, mutex *m2, int ordenv2){
	int x;
	if(ordenv1 < ordenv2) {
		lock(m1); lock(m2);
	} else {
		lock(m2); lock(m1);
	}
	x=v1+v2;
	unlock(m2);
	unlock(m1);
}
```

3. En evitación se intenta prevenir que el sistema entre en una situación de interbloqueo conociendo el estado del sistema y los recursos que los procesos pueden reservar en el futuro. Requiere conocer a priori el uso de recursos que va a hacer un proceso, lo que limita mucho su uso.