# Añadir limites a nuestras consultas

Si necesitamos obtener una cierta cantidad de resultados que cumplan algunos requisitos podemos hacer lo siguiente:

* En vez de hacer esto:
```sql
SELECT * FROM productos
WHERE productoID >= 15 AND productoID < 20
```

* Hacemos esto:
```sql
SELECT * FROM productos
WHERE productoID >= 15
LIMIT 5
```

Otra cosa interesante es que esos mismos 5 resultados que estamos limitando pueden ser aleatorios:

```sql
SELECT * FROM productos
WHERE productoID >= 15
ORDER BY RANDOM()
LIMIT 5
```

## OFFSET 

Esto establece un punto de partida, es decir desde donde se van a empezar a mostrar los resultados. Ejemplo de una tabla de 10 registros queremos que nos muestre 3 registros pero que se saltee los 3 primeros.

```sql
SELECT * FROM Users
LIMIT 3 OFFSET 3
```