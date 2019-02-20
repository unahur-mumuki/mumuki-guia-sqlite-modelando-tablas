Otra forma de hacerlo es definiendo la primary key al final de todos los campos:

```sql
CREATE TABLE Infraccion (
  id int NOT NULL PRIMARY KEY,
  cantidadPuntosDescontados int DEFAULT 0,
  monto decimal NOT NULL,
  observacion varchar(255)
  PRIMARY KEY (id)
)
```

