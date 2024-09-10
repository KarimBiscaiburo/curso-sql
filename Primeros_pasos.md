# Primeros Pasos

## Crear una base de datos

Aunque el browser de sqlite nos permite crear una base de datos sin ejecutar código, es necesario saber como funciona internamente esto, y el código que se utiliza es el siguiente: CREATE DATABASE "NOMBRE"

## Tablas

Las tablas son la representación de las entidades, y estas son, a su vez, las que conforman una base de datos. Por otro lado, es una estructura de datos que organiza su información con filas y columnas.

## Campos

Los campos, dentro de una tabla, son el nombre de una columna.

## Registros

Así como los campos son el nombre que tiene una columna, los registros son los nombres que tienen una fila. Pero tambien, cada registro va a contener la información de todos los campos. Por ejemplo, dentro de una tabla usuarios podemos tener los campos nombre, apellido y edad, y un registro va a referenciar a un item diferente pero que tengan el valor de los campos nombre, apellido y edad.

## Tipos de datos

Cuando estamos definiendo las tablas vamos a necesitar especificar que tipo de dato se va a almacenar en ese campo, y los tipos de datos que existen son los siguiente: 

> [!IMPORTANT]
> En sqlite son los que voy a nombrar abajo, pero en otros gestores de bases de datos pueden ser diferentes o mas.

* INTEGER: Sirve para almacenar datos numericos.
* TEXT: Sirve para almacenar datos de texto.
* BLOBL: Sirve para almacenar datos binarios, como archivos.
* REAL: Sirve para almacenar datos de tipo FLOAT, numeros con coma (2.5). (más rápido - menos capacidad para guardar numeros muy grandes)
* NUMERIC: Sirve para almacenar datos numericos que necesitan una precisión numerica muy alta (PI). (más lento - sin limite de capacidad)

## Propiedades de un campo

* DEFAULT: Valor por defecto que se le va a asignar si no es recibido un valor.
* PK: Primary Key, nos sirve para identificar, dentro de una tabla, cada registro asegurandonos no tener registros duplicados
* AI: Auto Increment, esto sirve principalmente cuando vamos a crear identificadores y que por cada registro vaya incrementando el valor. A su vez, esta es una propiedad de las claves primarias o PK
* NN: Not Null, significa que este campo no puede estar vacío

## Creando la primera tabla

Siguiendo todo lo aprendido anteriormente vamos a crear una tabla "usuarios", con los campos nombre, apellido y edad. El código es el siguiente:

```sql
CREATE TABLE usuarios (
	"usuarioID" INTEGER,
	"nombre"	TEXT,
	"apellido"	TEXT,
	"edad"	INTEGER,
	PRIMARY KEY("usuarioID" AUTOINCREMENT)
);
```

## Obtener datos a una tabla

Para obtener datos a una tabla, lo primero que necesitamos saber es como realizar consultas (las consultas son todos aquellos comandos que nos permiten realizar alguna acción en la base de datos). Para ello existe la sentencia "SELECT" la cual nos permite seleccionar algo, aunque tambien podemos seleccionar todo utilizando un "*" (SELECT *) o podemos seleccionar por valores de campos, luego debemos indicar de donde queremos seleccionar (referencia a una tabla), utilizamos la sentencia "FROM" y el nombre de la tabla (en mi caso cree la tabla "usuarios") "SELECT * FROM usuarios".

## Agregar datos a una tabla

Para esto utilizamos la consulta "INSERT INTO (tabla)" y luego entre parentesis tenemos que poner los campos que vamos a rellenar, "INSERT INTO usuarios (nombre,apellido,edad), despues podemos agregar los valores que queremos insertar tambien entre parentesis.

```sql
INSERT INTO usuarios (nombre,apellido,edad)
VALUES ("Martin","Perez",15)
```

Tambien podemos insertar varios registros en una misma sentencia, separando por "," cada uno.

```sql
INSERT INTO usuarios (nombre,apellido,edad)
VALUES ("Martin","Perez",15), ("Gaston","Hernandez",56)
```

## Identificadores

Estos nos sirven principalmente para diferenciar un registro de otro que puede llegar a tener los mismos valores. Por lo general se crea un campo nuevo llamado "id_(nombreTabla)" en nuestro caso "id_usuarios".

Cuando en una tabla (turnos_medicos) queremos hacer referencia a un identificador de otra tabla (pacientes), una buena practica es ponerle el mismo nombre de ese identificador, por ejemplo id_paciente

## Eliminar registros de una tabla

La forma mas sencilla es utilizando la consulta "DELET FROM (tabla)"

## Claves foraneas - Foreing key

Estos son unos identificadores que se utilizan en algunas tablas para hacer referencia a una clave primaria de otra tabla