Te dejamos la sentencia que crea la tabla del ejercicio anterior:

```sql
CREATE TABLE Infraccion (
  id int NOT NULL PRIMARY KEY,
  cantidadPuntosDescontados int DEFAULT 0,
  monto decimal NOT NULL,
  observacion varchar(255)
);
```