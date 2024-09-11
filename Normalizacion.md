# Normalización de bases de datos

Este es un proceso dentro de lo que es el diseño de una base de datos que nos sirve para eliminar anomalias en los datos, hacer que la base de datos sea mas eficiente y que nos permita realizar consultas mas efectivas, esto para tener un sistema mas escalable y sostenible a lo largo del tiempo.

La forma mas fácil de dividirlo es en 5 niveles, a estos niveles se los llaman "forma normal":

* Primera forma normal (1NF): Consiste en garantizar que cada atributo (columna) en una tabla contenga un único valor atómico, lo que significa que estos valores no pueden ser conjuntos, listas o cualquier tipo de datos que contenga una estructura de datos compleja dentro. Tambien establece que no deberían haber valores repetidos en una misma fila para una clave primaria, es decir, cada atributo debe tener una valor único para cada registro. 

Ejemplo:

✅: Creamos una tabla usuarios con los campos (id, nombre, apellido y teléfono).
❌: Creamos una tabla usuarios con los campos id e (info_empleados).

* Segunda forma normal (2NF): Esta norma establece que cada atributo que no sea una clave debe depender completamente de la clave primaria. Esto trata de eliminar las dependencias parciales, que es cuando un atributo depende solo en algunos aspectos de la clave primaria.

Ejemplo:

❌: Supongamos que tenemos una tabla con los campos (PedidoID, ClienteID, fecha de pedido, ProductoID, nombre del producto, precio del producto y cantidad del producto). Esto esta mal, ya que (nombre del producto, precio del producto y cantidad del producto) dependen del PedidoID y del ProductoID.
✅: Para que esto este bien, se deberia crear una tabla separada de productos con los atributos (ProductoID, nombre del producto y precio del producto).

* Tercera forma normal (3NF): Establece que cada atributo debe depender directamente de la clave primaría y no de atributos que no son claves. En otras palabras, no debe haber dependencias transitivas, y esto ocurre cuando un atributo "A" depende de otro atributo "B" y el atributo "B" depende de la clave primaria "C".

❌: En una tabla donde tenemos los atributos (ClienteID, nombre, codigo postal, ciudad y estado), ciudad y estado estan relacionados, por lo que ciudad depende funcionalmente de estado.
✅: Para solucionar esto deberiamos crear una segunda tabla con los atributos (UbicacionID, cuidad, estado, codigo postal) y la primera tabla quedaría (ClienteID, nombre UbicacionID)

* Cuarta forma normal (4NF): Es una forma en la que intentamos evitar la redundancia de datos y las anomalias de actualización. Esta establece que cada tabla debe tener una clave primaria compuesta que consta de multiples columnas en vez de una sola. Esto trata de solucionar las dependencias multivaluadas, y estas ocurren cuando una tabla tiene multiples valores para una columna, y no solo eso, sino que esos valores estan tambien relacionados con multiples valores de otras columnas de la misma tabla.

❌: Supongamos que tenemos la siguiente tabla (ProductoID, nombre, categoria, subcategoria), categoría y subcategoría estan relacionadas, lo que significa que una subcategoría pertenece solamente a una categoría, pero un producto puede tener varias subcategorías, esto crea una dependencia multivaluada.
✅: Para aplicar bien esta norma debemos separar las tablas en 2, una con los atributos (PrincipalID y nombre principal) y (SubcategoriaID, PrincipalID y nombre subcategoria)

* Quinta forma normal (5NF): En esta forma normal se asegura que no hay dependencias de unión entre los atributos, basicamente si un atributo depende de que se unan varios atributos de varias tablas, entonces debe ser movido a otra tabla. 