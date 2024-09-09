# Condiciones con AND y OR

Estas sirven para realizar varias condiciones, que se cumplan ambas o una de las dos

```sql
SELECT * FROM productos
WHERE productoID >= 15 AND productoID < 20
```

```sql
SELECT * FROM empleados
WHERE nombre = "Martin" OR nombre = "Jesus"
```

En este último caso se pueden llegar a cumplir ambas condiciones, por lo que se mostrarían ambas.

```sql
SELECT * FROM empleados
WHERE precio < 20 OR categoriaID = 6 AND proveedorID = 2
```

Si nosotros ejecutamos esta última consulta, se va a estar evaluando que el precio sea menor a 20 o que categoriaID sea 6 y proveedorID sea 2. Pero en caso que querramos evaluar que el precio sea menor a 20 o la categoriaID sea 6, y por otro lado, que proveedorID sea 2, debemos agregar parentesis.

```sql
SELECT * FROM empleados
WHERE (precio < 20 OR categoriaID = 6) AND proveedorID = 2
```

## Negar condiciones

```sql
SELECT * FROM productos
WHERE NOT productoID >= 15
```