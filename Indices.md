# Indices

Los indices tienen el objetivo de mejorar el rendimiento de las consultas en una base de datos organizandolos correctamente. Se encargan de organizar la información de manera mas efectiva para que cuando hagamos las consultas sean mas optimas. Existen distintos tipos de indices, los únicos y los no únicos.

* Únicos: Uno de estos indices son las llaves primarias, los cuales no permiten tener valores nulos y nos permiten identificar cada registro de manera única. Y por otro lado podemos crear ínices únicos que no sean llaves primarias

* No únicos

> [!NOTE]
> Tambien tenemos los índices ordinarios, que son aquellos que nos permiten optimizar las consultas pero permiten valores repetidos o nulos <br>
> Una de las desventajas de crear índices es el espacio en disco que ocupa crearlos. <br>
> Es bueno agregar índices a las llaves foraneas ya que por lo general son las que utilizamos para realizar consultas y unir tablas. Estos se crean automaticamente cuando asignamos una llave foranea <br>
> Una buena manera de nombrar los índices es "idx_nombreTabla_campo" "idx_orderDetails_quantity"


## Crear índices

Nosotros podemos crear índices para que nos sirvan de referencia a la hora de hacer consultasd. Esto nos permite realizar consultas más rápidas ya que le estamos agregando al sistema un índice que puede usar para obtener datos mas eficientemente.

```sql
CREATE INDEX nombre ON tabla (campo)
```

Por otro lado tal vez nosotros querramos crear índices únicos, ademas de los ID. Por ejemplo, tenemos una tabla de usuarios con su respectivo ID, nombre, apellido, email, etc, pero el email tambien debe ser único, pero a su vez tampoco queremos que sea la llave primaria ya que para eso tenemos el ID. Esto se puede hacer de la siguiente manera:

```sql
CREATE UNIQUE INDEX email ON tabla (user_email)
```

Ademas esto nos va a permitir agregar los valores que querramos pero sin que se repitan, en caso que querramos insertar un registro repetido, la consulta no se va a completar.

Tambien podemos crear índices compuestos, para que dos campos no puedan ser iguales, es decir, tenemos campo nombre y apellido, y pueden existir personas con un nombre o apellido igual, pero no personas con el mismo nombre y apellido.

```sql
CREATE UNIQUE INDEX fullname ON tabla (FirstName, LastName)
```

## Borrar índices

```sql
DROP INDEX nombre 
```