# JOINS

Estos se utilizan para combinar información de dos o mas tablas en una base de datos, pero que esa información se devuelva en una sola tabla. La mayoría de los JOINS devuelven productos cartesianos, los cuales son el resultado de combinar todas las filas de una tabla con todas las filas de otra tabla, creando todas las posibles combinaciones entre ellas. Esto sucede cuando no se especifica una condición de relación entre las tablas (como un JOIN con una cláusula ON o una cláusula WHERE).

Hay 4 tipos de JOINS mas comúnes:

* INNER JOINS
* RIGHT JOINS
* LEFT JOINS
* FULL JOINS

Tambien hay otros como los CROSS JOINS pero no son los mas típicos.

## INNER JOIN

Cuando unimos dos tablas mientras se cumpla una condición (con la clausula WHERE), quiere decir que estamos utilizando un INNER JOIN

Existen dos maneras de realizar un INNER JOIN, implicita y explicita:

* Implicita

```sql
SELECT * FROM Employees AS e, Orders AS o
WHERE e.EmployeesID = o.EmployeesID
```

> [!NOTE]
> Si no utilizamos el WHERE estariamos usando un CROSS JOIN implicito

* Explicita

```sql
SELECT * FROM Employees AS e
INNER JOIN Orders AS o
ON e.EmployeesID = o.EmployeesID
```

> [!NOTE]
> El "ON" actuaria como el WHERE, que seria la condicion de unión. Ademas, se podría obviar la palabra INNER y sería lo mismo.


## LEFT JOIN

Este nos devuelve toda una tabla y parte de la otra, es decir, tenemos la tabla "A" y la tabla "B", entonces nos va a mostrar toda la tabla A y si hay alguna coincidencia en la tabla B la va a mostrar, en caso que no se va a rellenar con campos nulos

```sql
SELECT FirstName, Reward, Month FROM Employees AS e
LEFT JOIN Rewards AS r ON e.EmployeesID = r.EmployeesID
```

## RIGHT JOIN

Cumple la misma función que LEFT JOIN pero con la tabla "B".

```sql
SELECT FirstName, Reward, Month FROM Employees AS e
RIGHT JOIN Rewards AS r ON e.EmployeesID = r.EmployeesID
```

> [!IMPORTANT]
> En sqlite no se puede hacer un RIGHT JOIN, pero podemos hacer lo mismo que como si fuera un LEFT JOIN, solo que a la inversa

```sql
SELECT FirstName, Reward, Month FROM Rewards AS r
LEFT JOIN Employees AS e ON e.EmployeesID = r.EmployeesID
```

## FULL JOIN

Devuelve ambas tablas completas combinadas, aunque tengan campos nullos.

```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;
```

> [!IMPORTANT]
> Este ejemplo es sacado de otra fuente, ya que en sqlite tampoco se puede hacer el FULL JOIN, pero si se puede simular de la siguiente manera:

```sql
SELECT FirstName, Reward, Month FROM Employees AS e
LEFT JOIN Rewards AS r ON e.EmployeesID = r.EmployeesID

UNION

SELECT FirstName, Reward, Month FROM Rewards AS r
LEFT JOIN Employees AS e ON e.EmployeesID = r.EmployeesID
```



## CROSS JOIN

Estos se utilizan para juntar 2 o mas tablas pero obteniendo un resultado cartesiano. Es una manera mas explicita de hacerlo, aunque tambien se puede hacer de manera implicita:

* Explicita:

```sql
SELECT * FROM Products
CROSS JOIN Orders
```

* Implicita:

```sql
SELECT * FROM Products, Orders
```