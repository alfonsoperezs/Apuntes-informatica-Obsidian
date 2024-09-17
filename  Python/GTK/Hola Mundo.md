```python
#!/usr/bin/env python3
from __future__ import annotations 

import gi
gi.require_version('Gtk', '4.0')
from gi.repository import Gtk

APPLICATION_ID: str = 'es.udc.fic.ipm.helloworld' #En python no existen las constantes, por tanto ponemos el nombre de una variable en mayúsculas para indicar que se va a usar como constante
WINDOW_PADDING: int = 24

#Creamos la interfaz (una ventana con etiquetado):
def on_application_activate(app: Gtk.Application) -> None:
    win = Gtk.ApplicationWindow(title= "The Mythical Hello World") #si quieres una ventana creas una ApplicationWindow, podemos meterle un título
    label = Gtk.Label( #widget de texto
        label= "Hello World!",
        margin_top = WINDOW_PADDING,
        margin_end = WINDOW_PADDING,
        margin_bottom = WINDOW_PADDING,
        margin_start = WINDOW_PADDING,
    )
    win.set_child(label) #Creamos la etiqueta y metemos la ventana dentro
    app.add_window(win) #Metemos la ventana que hemos creado a la aplicación
    win.present() #Por defecto las ventanas son invisibles

#BUCLE DE EVENTOS, COMÚN A TODAS LAS LIBRERÍAS, se ejecuta siempre que esté la aplicación abierta (bucle infinito hasta que cierres todas las ventanas de la aplicación):
if __name__ == '__main__':
    app = Gtk.Application(application_id= APPLICATION_ID)
    app.connect('activate', on_application_activate)
    app.run(None) #Este método inicializa la librería y entra en el bucle de eventos
```
