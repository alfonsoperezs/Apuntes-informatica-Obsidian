Utilizando la línea de comandos de Windows:

1. Escribe `diskpart`
2. Escribe `list disk`
	Aparecerá una tabla como la siguiente donde debes fijarte el número de la unidad que quieres formatear.
	![[Captura de pantalla (15).png]]
3. Selecciona el disco con el comando `select disk [número]`.
4. Escribe `clean` y a continuación `create partition primary`.