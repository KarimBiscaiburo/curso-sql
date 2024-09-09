# Operador Between

Es un operador que se utiliza para seleccionar valores dentro de un rango especifico, con cualquier tipo de dato pero siempre y cuando sea compatible con el operador. 

```sql
SELECT * FROM productos 
WHERE precio BETWEEN 20 AND 40
AND categoria = 1
OR tipoCarne = "pollo"
```

Tambien se puede utilizar para buscar entre fechas

```sql
SELECT * FROM empleados 
WHERE cumpleanios BETWEEN "1960-0-1" AND "1970-0-1"
```
> [!NOTE]
> Los limites estan incluidos y el primer valor no puede ser mayor que el segundo valor. 