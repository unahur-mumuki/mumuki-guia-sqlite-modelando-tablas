¡Muy bien! Definiste tu primera tabla (bueno, con algo de ayuda...).

En el ejemplo elegimos definir a `id` como PK en la misma línea, pero es posible también hacerlo al final. Quedaría así:

```sql
CREATE TABLE Infraccion (
  id int NOT NULL,
  cantidadPuntosDescontados int DEFAULT 0,
  monto decimal NOT NULL,
  observacion varchar(255),
  PRIMARY KEY (id)
)
```

