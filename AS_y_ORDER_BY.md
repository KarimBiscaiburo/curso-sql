## AS

Esta sentencia nos permite modificar el nombre de un campo. Por ejemplo:

```sql
SELECT lastname AS apellido, firstname AS nombre FROM usuarios
```

> [!NOTE]
> Esto no modifica el nombre del campo en la tabla en si, sino que la modifica en la nueva tabla que vamos a obtener.

## ORDER BY

Esta clausula nos permite utilizar diferentes filtros para ordenar. Por defecto las tablas se ordenan por el id de forma ascendente, pero si nosotros queremos recibir esa nueva tabla de otra manera debemos utilizar esta clausula, la cual en el caso de los números, tambien se ordenan de manera ascendente si no especificamos lo contrario.

Por ejemplo:

```sql
SELECT * FROM productos
ORDER BY precio ASC 
```

* ASC: Ascendente
* DESC: Descendente

### Gerarquía 

El peso que tiene cada tipo de caracter a la hora de ordenar es el siguiente:

* El que menor peso tiene es el "NULL", es decir, el que primero se va a mostrar en un orden ascendente
* Luego estan los números
* Luego estan los caracteres especiales
* Y por último estan las letras

### No mostrar los NULLS

Es posible que querramos mostrar los datos de manera ascendente pero que los datos nulos vayan al final, para esto usamos la siguiente consulta:

```sql
SELECT * FROM productos
ORDER BY nombre ASC NULLS LAST
```

Por defecto es como poner:

```sql
SELECT * FROM productos
ORDER BY nombre ASC NULLS FIRST
```

### Mostrar ordenados de manera aleatoria

```sql
SELECT * FROM productos
ORDER BY RANDOM() 
```

### Ordenar con varios filtros

```sql
SELECT * FROM productos
ORDER BY precio ASC, nombre DESC
```
Esto tiene una "gerarquía" tambien, por lo que primero va a ordenar por precio, pero en caso que haya algun producto sin precio, lo va a ordenar por nombre de manera descendente
