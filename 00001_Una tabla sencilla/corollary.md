Otra forma de hacerlo es definiendo la primary key al final de todos los campos:

```sql
CREATE TABLE Infraccion (
  id int(10) NOT NULL AUTO_INCREMENT,
  cantidadPuntosDescontados tinyint(3) DEFAULT NULL,
  monto decimal(8,2) NOT NULL,
  observacion varchar(255) DEFAULT NULL,
  PRIMARY KEY (id)
)
```

