# Bloqueos y transacciones

Los bloqueos son una especie de mecanismo que tienen las bases de datos para poder manejar mejor los accesos concurrentes a las bases de datos. Estos son utilies cuando por ejemplo dos personas quieren actualizar un mismo registro al mismo tiempo.

Cada gestor de bases de datos tiene sus propios bloqueos, o tambien permite definir el tipo de bloqueo.

## Tipos de bloqueos

### Shared Locks

También conocidos como bloqueos de lectura. Basicamente es un bloqueo donde nadie puede escribir pero si leer, es decir, este bloqueo se aplica cuando alguien esta leyendo, mientras alguien lo este haciendo no se va a poder escribir sobre la base de datos pero si van a poder leer en simultaneo.

### Reserved Locks

Este bloqueo se aplica cuando alguien quiere escribir en la base de datos, y restringe que otras conexiones puedan escribir tambien, pero si permite que otras conexiones puedan leer.

### Exclusive Locks

Este bloqueo se aplica cuando alguien esta escribiendo en la base de datos, y restringe que cualquier otra conexion pueda leer o escribir.

## Trasacciones

Las transacciones son una forma de realizar consultas y manejar el proceso desde que se inicia hasta que se ascienta el cambio. Esto es útil cuando estamos haciendo consultas de tipo INSERT, UPDATE y DELETE. 

Para iniciar una transacción utilizamos la sentencia "BEGIN;":

```sql
BEGIN;
```

> [!NOTE]
> Cuando nosotros iniciamos una transacción de esta manera es como si estuvieramos escribiendo "BEGIN TRANSACCIÓN" solo que "TRANSACCIÓN" seria reemplazada por una consulta

Luego realizamos una consulta:

```sql
BEGIN;

UPDATE Productos SET ProductName = "Tomate";
```

En este caso nos hubieramos equivocado al actualizar ProductName, ya que al no especificar la condición estariamos actualizando todos los registros, provocando la perdidad de los datos. Por suerte hay una manera de devolver estos cambios que se iniciaron dentro de una transacción.

```sql
ROLLBACK
```

Ahora podriamos volver a ejecutar la consulta pero con la sentencia correcta.

```sql
BEGIN;

UPDATE Productos SET ProductName = "Tomate" WHERE ProductName = "Lechuga";
```

Una vez que el cambio fue realizado con exito podemos ascentar la consulta.

```sql
COMMIT
```

Igualmente esto se podría realizar en un solo comando.

```sql
BEGIN;

UPDATE Productos SET ProductName = "Tomate" WHERE ProductName = "Lechuga";

COMMIT
```

> [!IMPORTANT]
> Estas cosas no se suelen hacer dentro de una consola de sql, sino mas bien del lado del servidor de una aplicación , para poder tener un control mas detallado del estado de las consultas y revertir algun cambio si ocurre un error.