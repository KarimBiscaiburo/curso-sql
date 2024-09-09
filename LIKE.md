# Operador LIKE

Este tambien es un operador de comparación que sirve para buscar y filtrar registros en función de ciertos patrones de cadena de texto. El comparador LIKE se parece a las expresiones regulares pero este es mucho mas simple y limitado. A su vez permite realizar busquedas de texto parcial utilizando algo que se llama "caracter comodin". 

> [!NOTE]
> Dependiendo que gestor de BD estemos utilizando puede que hayan comodines diferentes, en SQLite existen 2 ( % y _ )

Por defecto, utilizar un LIKE es lo mismo que utilizar un "="

```sql
SELECT * FROM empleados
WHERE apellido LIKE "Martinez"
```

```sql
SELECT * FROM empleados
WHERE apellido = "Martinez"
```

La diferencia es que con el LIKE tenemos los comodines

* El "%" quiere decir que pude haber algo mas antes o despues del texto. Por ejemplo: <br>
( %r ) Esto significa que tiene que terminar con "r" <br>
( r% ) Esto significa que tiene que empezar con "r" <br>
( %r% ) Esto significa que tiene que contener la "r"

* El "_" hace referencia a un caracter cualquiera. Por ejemplo <br>
( "F__" ) Esto quiere decir que buscamos una palabra que empiece con "F" y le sigan 2 caracteres cualquiera <br>
( "__f" ) Esto quiere decir que buscamos una palabra que termine con "F" y antes tenga 2 caracteres cualquiera

```sql
SELECT * FROM empleados
WHERE apellido = "M__%"
```

```sql
SELECT * FROM Categories 
WHERE CategoryName LIKE "C__%ion_"
```