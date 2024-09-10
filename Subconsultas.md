# Subconsultas

Las subconsultas son muy utiles principalmente cuando necesitamos relacionar tablas para obtener un resultado que requiera datos de 2 o mas tablas. No es la mejor manera para relacionar tablas porque existen los JOINS que nos permiten hacer esto justamente, pero hay ocaciones en las que son 100% necesarias.

Un ejemplo claro sería: 

```sql
SELECT (SELECT col1 FROM x), col2, col3 FROM y
```

En este caso estamos seleccionando varias columnas de la entidad "y" pero a su vez, la primera columna es un resultado de seleccionar la columna 1 de la entidad "x"

> [!IMPORTANT]
> Las subconsultas solo recuperan datos (SELECT), no podemos hacer subconsultas con un INSERT, UPDATE o DELETE. Si se puede hacer un INSERT, UPDATE o DELETE que dentro tenga una subconsulta.

Existen subconsultas de distintos niveles dependiendo la profundidad de la misma, es decir, una subconsulta dentro de una consulta sería una subconsulta de 1er nivel, una subconsulta dentro de otra subconsulta sería una subconsulta de 2do nivel, y así sucesivamente.

```sql
SELECT (
	SELECT ProductName FROM Products
	WHERE OrderDetails.ProductID = ProductID
) AS nombre,
Quantity FROM OrderDetails
```
> [!NOTE]
> Notemos como en el WHERE dentro de la subconsulta es necesario hacer referencia a otra tabla, ProductID, si no especificamos lo contrario, va a hacer referencia al que existe dentro de la tabla Products.

> [!WARNING]
> Dentro de una subconsulta no se pueden utilizar alias de un campo, es decir, no se puede hacer lo siguiente: <br>
>```sql
>   SELECT ProductID AS pID,
>   (
>	    SELECT ProductName FROM Products
>	    WHERE OrderDetails.pID = ProductID
>   ) AS nombre,
>   Quantity FROM OrderDetails
>``` 
><br> Pero si se puede hacer de una entidad:<br>
>```sql
>   SELECT ProductID AS pID,
>   (
>   	SELECT ProductName FROM Products
>	    WHERE OD.ProductID = ProductID
>   ) AS nombre,
>   Quantity FROM OrderDetails AS OD
>```

Ahora vamos a hacer un ejercicio un poco mas complicado:

* Necesitamos obtener el id de un producto, nombre del producto, precio unitario, cuantos se vendieron de cada producto y el total recaudado de cada producto. 

```sql
SELECT ProductID,
		 (SELECT ProductName FROM Products WHERE OD.ProductID = ProductID) AS nombre_producto,
		 (SELECT Price FROM Products WHERE OD.ProductID = ProductID) AS precio_unit,
		 SUM(Quantity) AS total_vendido,
		 (total_vendido * precio_unit)
FROM OrderDetails AS OD
GROUP BY ProductID
```

> [!WARNING]
> Esto nos va a dar un error, ya que en "total_vendido" no se puede hacer referencia a un alias fruto de una funcion de agregación, solo se podría dentro de un HAVING.

```sql
SELECT ProductID,
		 (SELECT ProductName FROM Products WHERE OD.ProductID = ProductID) AS nombre_producto,
		 (SELECT Price FROM Products WHERE OD.ProductID = ProductID) AS precio_unit,
		 SUM(Quantity) AS total_vendido,
		 SUM(Quantity) * precio_unit
FROM OrderDetails AS OD
GROUP BY ProductID
```

> [!WARNING]
> Esto tambien va a dar un error, ya que tampoco podemos hacer referencia a el alias "precio_unit" porque en el SELECT no se pueden utilizar alias para realizar operaciones matematicas. Tendríamos que hacer devuelta la consulta.

```sql
SELECT ProductID,
		 (SELECT ProductName FROM Products WHERE OD.ProductID = ProductID) AS nombre_producto,
		 (SELECT Price FROM Products WHERE OD.ProductID = ProductID) AS precio_unit,
		 SUM(Quantity) AS total_vendido,
		 SUM(Quantity) * (SELECT Price FROM Products WHERE OD.ProductID = ProductID) AS recaudacion
FROM OrderDetails AS OD
GROUP BY ProductID
```

> [!TIP]
> Las subconsultas tambien se pueden hacer dentro de un FROM, WHERE y otras condiciones o consultas