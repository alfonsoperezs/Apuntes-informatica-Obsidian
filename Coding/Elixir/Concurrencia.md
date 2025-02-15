## Procesos
En Elixir, los procesos son ligeros y aislados, ejecutándose de manera concurrente dentro de la BEAM (Erlang VM).
En Elixir, los procesos habitualmente mantienen estado mediante llamadas recursivas, pasando el estado como argumento de la función.
```erlang
def loop(primo, siguiente)
```
Además, los procesos tienen un mailbox (foto) donde almacenan los mensajes hasta que el proceso quiere recibir un mensaje.
### spawn()
`spawn` crea un nuevo proceso que ejecuta la función dada y devuelve su PID. 
#### Características
- El PID es fundamental para poder comunicar los procesos entre sí. 
- Es habitual pasarle una función anónima y escribir en ella el código que deseamos que ejecute. 
- Esta función siempre tiene éxito, por lo que debemos tener cuidado que si muere el proceso, el PID dejará de ser válido.

```erlang
pid = spawn(fn -> IO.puts("Hola desde otro proceso") end)
```
## Paso de mensajes entre procesos
### send()
`send` envía un mensaje a otro proceso.
#### Características
- El envío de mensaje es asíncrono, sigue con la ejecución, ya que no espera respuesta.
- Tiene siempre éxito, incluso aunque el proceso destino no exista.

```erlang
send(pid_destino, message)
```
#### Enviar mensajes con identificación del remitente
Si queremos que el proceso destino pueda saber quién le ha mandado el mensaje, podemos incluir el PID del remitente con `self()`:

```erlang
send(pid, {self(), message}) 
```
### receive()
`receive` se usa para extraer y procesar mensajes del mailbox de un proceso.
#### Características
- Permite manejar mensajes asincrónamente, esperando hasta que llegue uno que coincida con un patrón.
- A diferencia de `send`, es bloqueante. Si un mensaje no encaja, se queda esperando.

```erlang
receive
	pattern_1 value ... -> ...
	pattern_2 value ... -> ...
```