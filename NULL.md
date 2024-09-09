# Operador IS NULL y IS NOT NULL

Son basicamente operadores que nos permiten filtrar por si los campos estan vacios o no

```sql
SELECT * FROM Categories 
WHERE CategoryName IS NOT NULL
ORDER BY CategoryID ASC
```

```sql
SELECT * FROM Categories 
WHERE CategoryName IS NULL
ORDER BY CategoryID ASC
```