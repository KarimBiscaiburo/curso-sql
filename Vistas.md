# Vistas

Las vistas son tablas virtuales que se crean a partir de una consulta SELECT que se ejecuta sobre una o varias tablas. Estas no es que almacenan datos, sino que son como una referencia a una consulta. Esto es muy util cuando necesitamos interactuar con consultas muy grandes y complejas, mas que nada para que a partir del resultado de esa consulta podamos realizar otras consultas y usemos esa referencia para no tener que ejecutar esa consulta tan compleja varias veces. 

Tambien se pueden restringir los datos que queremos mostrarle a los usuarios.

## Crear una vista

```sql
CREATE VIEW Productos_simplificados AS
-- Consulta que sobre la que crearemos la vista
SELECT ProductoID, ProductName, Price FROM Products
WHERE ProductID > 20
ORDER BY ProductID DESC
```

Ahora esta "nueva tabla" la podemos utilizar como una tabla mas

```sql
SELECT * FROM Productos_simplificados
```

> [!WARNING]
> Tenemos que tener en cuenta que al usar estas vistas no se estan creando nuevas tablas, simplemente se ejecuta el codigo al que hacemos referencia con esa vista, solamente que nosotros no lo vemos, por eso hay que saber que esto no es conveniente para usar en todos los casos ya que consume recursos

## Eliminar una vista

```sql
DROP VIEW Productos_simplificados
```

* Recomendada: Tener en cuenta los temas de rendimiento

```sql
DROP VIEW IF EXISTS Productos_simplificados
```