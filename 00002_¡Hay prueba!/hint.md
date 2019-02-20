Te dejamos la sentencia que crea la tabla del ejercicio anterior:

```sql
CREATE TABLE Infraccion (
  id int(10) NOT NULL PRIMARY KEY,
  cantidadPuntosDescontados tinyint(3) DEFAULT NULL,
  monto decimal(8,2) NOT NULL,
  observacion varchar(255) DEFAULT NULL
);
```