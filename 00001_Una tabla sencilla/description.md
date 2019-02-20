
```sql
CREATE TABLE Infraccion (
  id int(10) unsigned NOT NULL AUTO_INCREMENT PRIMARY KEY,
  cantidadPuntosDescontados tinyint(3) unsigned DEFAULT NULL,
  monto decimal(8,2) unsigned NOT NULL,
  observacion varchar(255) DEFAULT NULL
)
```

