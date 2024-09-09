# Clausulas GROUP BY y HAVING

Estas dos clausulas sirven para trabajar con grupos, mas convenientemente cuando usamos funciones de agregación que justamnente nos devuelven grupos, ya que por ejemplo, con un WHERE o condiciones, no se podria trabajar sobre estos, porque lo hacen con registros/filas, no grupos.

## GROUP BY

Esta clausula se utiliza para agrupar uno o varios registros según uno o varios valores de las columnas, por lo que es necesario hacer todos los filtrados y condiciones antes de agrupar los registros. Por ejemplo:

```sql
SELECT SupplierID, round(avg(Price)) AS promedio FROM Products
GROUP BY SupplierID
ORDER BY promedio DESC
```

En este caso estamos haciendo una consulta para que nos devuelva una tabla con el SupplierID y el promedio de los productos de cada SupplierID ordenado por ese promedio de manera descendente.

## HAVING

Es una clausula que nos permite hacer filtrados de grupos, asi como el WHERE nos permite filtrar registros. A su vez, esta se utiliza siempre que exista la clausula de GROUP BY porque al ser una clausula que funciona con grupos, si nosotros no agrupamos previamente los resultados estariamos trabajando con filas, y HAVING no trabaja con filas

```sql
SELECT SupplierID, round(avg(Price)) AS promedio FROM Products
GROUP BY SupplierID
HAVING promedio > 40
ORDER BY promedio DESC
```

```sql
SELECT ProductID, SUM(Quantity) as total_vendido FROM OrderDetails
GROUP BY ProductID
HAVING total_vendido > 50
ORDER BY total_vendido
```