## Cabezas y colas
#### Ejemplo 1
```
iex(6)> [h | t] = [1,2]
[1, 2]
iex(7)> h
1
iex(8)> t
[2]
```
#### Ejemplo 2
```
iex(9)> [h | t] = [1, 2, 3, 4, 5]
[1, 2, 3, 4, 5]
iex(10)> h
1
iex(11)> t
[2, 3, 4, 5]
```