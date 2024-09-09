# Funciones de Agregación

Estas son funciones que nos permiten agrupar datos, resumirlos e incluso trabajar con estadisticas sobre estos datos. Estas se utilizan con la clausula SELECT.

```sql
SELECT function()
```

* Cuenta la cantidad de registros "ProductName" que existen dentro de "Products"

```sql
SELECT count(ProductName) FROM Products
```

* Suma los precios de "Price" que existen dentro de "Products"

```sql
SELECT SUM(Price) FROM Products
```

* Saca el promedio de "Price" dentro de "Products"

```sql
SELECT avg(Price) FROM Products
```

* Redondea el promedio de "Price" dentro de "Products"

```sql
SELECT round(avg(Price)) AS promedio_redondeado FROM Products
```

> [!IMPORTANT]
> No se puede usar una función de agregación que utilice un valor que sea un resultado de otra función de agregación. En otras palabras, no se puede realizar una función de agregación que contenga una función de agregación. Hay una manera, que sería hacer subconsultas.