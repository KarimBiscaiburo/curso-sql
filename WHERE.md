# Condiciones y clausula WHERE

Las condiciones nos permiten filtrar los resultados o registros a los que queremos acceder para realizar una consulta. Esto es muy util principalmente cuando necesitamos eliminar un usuario.

```sql
SELECT nombre FROM productos
WHERE productoID = 15
```

Dentro de la condición necesitamos indicar lo que queremos evaluar "productoID" y la condición que debe cumplir "= 15".

Tambien nos puede servir para actualizar algun dato de un registro:

```sql
UPDATE turnos_medicos 
SET horario = "10:30",
motivo = "Dolor de cabeza"
WHERE idTurno = 3
```