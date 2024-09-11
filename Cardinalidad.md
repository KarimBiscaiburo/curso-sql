# Cardinalidad

La cardinalidad se utiliza para especificar la relación que hay entre dos entidades, y existen 3 tipos de cardinalidades:

* De 1 a 1 ( 1:1 )
* De 1 a muchos o muchos a 1 ( 1:n ) ( n:1 )
* Muchos a muchos ( n:n )

## 1:1

Un registro en una tabla se relaciona exactamente con otro registro de otra tabla. Ejemplo, una persona tiene un único documento y ese documento solo pertenece a esa persona

## 1:n - n:1

Es cuando un registro en una tabla se relaciona con varios registros de otra tabla o viceversa. Ejemplo, un escritor escribio varios libros.

## n:n

Es cuando varios registros de una tabla se pueden relacionar con varios registros de otras tablas. Ejemplo, un estudiantes pueden estar tomando varios cursos y un mismo curso puede ser tomado por varios estudiantes.

Como por lo general suele ser complicado relacionar estas tablas, se crea una tercera tabla que funcione como unión entre estas. Consiguiendo así, una relación 1:n. Por ejemplo, se crea una tabla inscripciones donde una inscripcion solo puede relacionarse con un estudiante y un curso, luego pueden haber mas inscripciones con valores repetidos pero la inscripcionID no va a ser la misma.
