# Notas del curso de SQL

* Curso Dalto: https://www.youtube.com/watch?v=DFg1V-rO6Pg

## Que es SQL?

Son las siglas de Structured Query Language (lenguaje de consultas estructuradas). A su vez, este es un lenguaje estandarizado, lo que quiere decir que al todos los gestores de bases de datos tienen que seguir este estandar, por lo que una vez que lo aprendemos ya nos va a servir para todo.

## Diagrama Entidad Relación - Con Notación de Chen

Cuando trabajamos con bases de datos nos vamos a topar con algúnos objetos, estos podrían ser las entidades, las cuales son como un objeto que hacen referencia a cualquier cosa o concepto que podamos tener en la vida real, las cuales son representadas por tablas y por lo tanto, las entidades son una representación de algo. Para dar un ejemplo mas claro, cuando nosotros hacemos un dibujo de una casa, este dibujo no es una casa en realidad, sino mas bien una representación de la casa.

Las entidades lo que hacen es almacenar información de entidades en bases de datos. Por ejemplo, una entidad "persona" va a almacenar todos los datos de una persona.

La nomenclatura que se utiliza para representar las entidades se llama notación de chen, y son basicmamente una manera de representar las entidades y sus relaciones.

Dentro de la notación de chen las entidades se dibujan con una palabra encerrada por un cuadrado. 

### ¿Qué es lo que hace que una entidad sea una entidad

Una entidad es una entidad dado sus atributos, los cuales dentro del ejemplo de la casa podrian ser, ambiente, baños, dirección, propietario, etc. Estos atributos son representados por un obalo, pero tambien existen los atributos simples y compuestos.

Los datos simples son aquellos que solamente tienen datos únicos, es decir, no estan compuestos por nada mas que solo ese dato, por ejemplo el precio de una casa que puede ser 100.000.

Los datos compuestos son aquellos que pueden contener otro tipo de datos, por ejemplo los ambientes, que estan compuestos por otros atributos mas chicos, como el tamaño y el tipo de ambiente (comedor, dormitorio, baño).

La manera de diferenciar los atributos simples y compuestos es agregandoles a estos últimos sus respectivos atributos adicionales.

Tambien tenemos que saber que existen los atributos multivalor, que no son mas que atributos que pueden contener mas de un valor, como por ejemplo los ambientes, que pueden haber varios ambientes con diferentes caracteristicas. Estos se representan con dos obalos.

Por último estan los atributos derivados, los cuales con aquellos que pueden ser obtenidos por otros atributos. Por ejemplo, si tenemos antigüedad y fecha de construcción, la antigüedad podría sacarse con simplemente obtener la fecha de construcción. Estos se representan con un obalo pero con linea punteada.

Por otro lado existen las "Key" o llave en español, las cuales son una manera de identificar de forma única a una entidad, esto sirve para poder saber, dentro de una entidad "Casa", cuál es cual. Estos son datos que nunca se van a repetir dentro de la entidad. Y la manera de representarlas es con un obalo, pero con la palabra subrayada.
 
## Empezar a practicar

Como en el curso utiliza sqlite3, voy a detallar los pasos para la instalación:

* Ir a la página: https://www.sqlite.org/download.html
* Ir a "download" y descargar el archivo que diga "sqlite-tools..." dependiendo si es para windows, linux o mac.
* Copiar los archivos que se descargan, ir a la disco donde esta el sistema operativo instalado (en mi caso :C), crear una carpeta y pegar los archivos.
* Ahora necesitamos indicarle al sistema operativo que queremos acceder a la consola que nos brinda sqlite, desde cualquier ubicación. Para eso tenemos que editar las variables de entorno del sistema.
* En el buscador de Windows buscamos "Variables del sistema".
* Entramos a "variables de entorno"
* Dentro de las variables de nuestro usuario hacemos doble click en "path".
* Hacemos click en "nuevo" y agregamos la rula absoluta de donde agregamos los archivos de sqlite. En mi caso C:\sqlite3.
* Guardamos los cambios.
* Ahora necesitamos instalar Sqlite Browser: https://sqlitebrowser.org/dl/
* Instalamos la versión "Standar installer".