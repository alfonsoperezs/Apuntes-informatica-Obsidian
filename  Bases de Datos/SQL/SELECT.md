La sentencia `SELECT` le permite seleccionar u obtener datos de una o más tablas.

Sintaxis: `SELECT [DISTINCT|ALL] {* | <expr1> [, <expr2>] ...}`

Que se puede poner en el SELECT:
	- Columnas individuales: `SELECT col1, col2`
	- Todas las columnas: `SELECT *`
	- Expresiones aritmétricas o de cadena: `SELECT column1 + column2 AS total`
	- Valores únicos: `SELECT DISTINCT column1`



