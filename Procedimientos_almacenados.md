# Procedimientos almacenadoss

Es un conjunto de instrucciones o comandos que se guardan en la base de datos y que podemos ejecutarlas en cualquier momento. Esto es util cuando debemos realizar varios pasos, es decir, si cada vez que queremos realizar algun cambio debemos extraer datos, compararlos, unirlos y cambiarlos, es mucho mas util tener un procedimiento que nos realice estas operaciones automaticamente.

Estos procedimientos se guardan con un nombre y almacenan un conjunto de consultas, entonces cada vez que llamemos a ese nombre se van a ejecutar todas esas consultas.

Algunos de los beneficios son la reducción de código repetido, facilita la organización y mantenimiento del código, y mejora la seguridad ya que limita el acceso a la base de datos pasando por un procedimiento que ya sabemos que funciona.

Es similar a una función en lenguajes como Python, java, etc, pero con la sintaxis de SQL.