# Operador lógico IN

Este operador es como una abreviación al operador lógico OR. Supongamos que tenemos que filtrar por varios tipos de proveedores:

```sql
SELECT * FROM proveedores 
WHERE proveedoresID = 1
OR proveedoresID = 2
OR proveedoresID = 3
OR proveedoresID = 5
```

En consultas muy grandes, esto es muy tedioso. Lo bueno es que este operador, opera, sobre una tupla que es un conjunto de datos.

```sql
SELECT * FROM proveedores 
WHERE proveedoresID IN (1,2,3,5)
```

Lo mismo se puede hacer para filtrar que no sean esos los proveedores.

```sql
SELECT * FROM proveedores 
WHERE proveedoresID NOT IN (1,2,3,5)
```