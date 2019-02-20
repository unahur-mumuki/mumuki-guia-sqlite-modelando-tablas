Ya aprendimos a consultar, insertar, modificar y eliminar datos de una y varias tablas, pero... ¿cómo se crean las tablas?

En SQL todo se resuelve con una query, y la creación de tablas no es la excepción: existe una sentencia, `CREATE TABLE`, que sirve exactamente para hacer eso. 

Supongamos entonces que queremos crear una tabla para registrar infracciones de tránsito, con los siguientes datos:

* **id**, un número entero, obligatorio, que será nuestra PK;
* **cantidadPuntosDescontados**, un número entero con valor por defecto 0;
* **monto**, un número decimal, obligatorio;
* **observacion**, un texto de hasta 255 caracteres.
 
La consulta que tendríamos que escribir para lograrlo es la siguiente:

```sql
CREATE TABLE Infraccion (
  id int NOT NULL PRIMARY KEY,
  cantidadPuntosDescontados int DEFAULT 0,
  monto decimal NOT NULL,
  observacion varchar(255)
);
```

> Presioná "Continuar" para ver cómo se vería esta tabla. Ya cargamos algunos datos por vos.
