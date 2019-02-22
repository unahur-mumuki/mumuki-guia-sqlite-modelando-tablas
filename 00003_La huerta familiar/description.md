<div
  class='mu-erd'
  data-entities='{
    "origen": {
      "id": {
        "type": "Integer",
        "pk": true
      },
      "nombre *": {
         "type": "Text"
      },
      "pais *": {
        "type": "Text"
      },
      "latitud": {
        "type": "Decimal"
      },
      "longitud": {
        "type": "Decimal"
      }
    },
    "semilla": {
      "id": {
        "type": "Integer",
        "pk": true
      },
      "nombre *": {
        "type": "Text"
      },
      "anio *": {
        "type": "Integer"
      },
      "tolera_sombra *": {
        "type": "Boolean"
      },
      "origen_id": { 
        "type": "Integer",
        "fk": {
          "to": { "entity": "origen", "column": "id" },
          "type": "many_to_one"
        }
      }
    },    
    "planta": {
      "id": {
        "type": "Integer",
        "pk": true
      },
      "observaciones": {
        "type": "Text"
      },
      "fecha_siembra *": {
        "type": "Date"
      },
      "semilla_id": {
        "type": "Integer",
        "fk": {
          "to": { "entity": "semilla", "column": "id" },
          "type": "many_to_one"
        }
      }
    },
    "responsable": {
      "id": {
        "type": "Integer",
        "pk": true
      },
      "nombre *": {
        "type": "Text"
      },
      "edad *": {
        "type": "Integer"
      }
    },
    "planta_responsable": {
      "planta_id": {
        "type": "Integer",
        "pk": true,
        "fk": {
          "to": { "entity": "planta", "column": "id" },
          "type": "many_to_one"
        }
      },
      "responsable_id": {
        "type": "Integer",
        "pk": true,
        "fk": {
          "to": { "entity": "responsable", "column": "id" },
          "type": "many_to_one"
        }        
      }
    }     
  }'>
</div>

**Aclaraciones**

* Las columnas marcadas con un asterisco (*) son obligatorias, contemplarlo en el script de creación.
* Utilizar `AUTO_INCREMENT` en todas las claves primarias, excepto la de `planta_responsable` que es compuesta.
* Respetar los nombres de las tablas y los campos, ya que el script de inserción de datos provisto hará uso de ellos.

**Valores por defecto**:

* Fecha 21/09/2019 en `fecha_siembra` de Planta.
* Edad 18 en Responsable.

**Consultas**:

* Nombre y edad de los y las responsables mayores de 18 años de las plantas de cualquier variedad de zapallo. Pista: el nombre de la semilla tiene que contener el texto "zapallo".
* Plantas que no toleran sombra, sembradas en los ultimos 2 meses. Mostrar el nombre de la planta, el país de origen y la fecha de siembra.
* Nombre, lugar de origen y cantidad de usos de las tres semillas más utilizadas (o sea, las que más plantas tienen).

**Datos de prueba**

```sql
insert into origen (nombre, pais) values
  ("INTA Castelar", "Argentina"),
  ("Granja Ecológica Ventilla", "Bolivia"),
  ("Morón SurCo", "Argentina");

insert into semilla (nombre, anio, tolera_sombra, origen_id) values
  ("Zapallo Anco", 2017, false, 1),
  ("Zapallo Kabutia", 2018, false, 1),
  ("Zapallo Plomo", 2019, false, 3),
  ("Quirquiña", 2018, true, 2),
  ("Espinaca", 2016, true, 2);

insert into planta (fecha_siembra, semilla_id) values
  (NOW(), 1),
  (NOW(), 1),
  (SUBDATE(NOW(), 60), 1),
  (SUBDATE(NOW(), 90), 1),
  (NOW(), 2),
  (NOW(), 2),
  (SUBDATE(NOW(), 60), 1),
  (SUBDATE(NOW(), 45), 3),
  (SUBDATE(NOW(), 10), 3),
  (SUBDATE(NOW(), 70), 4),
  (SUBDATE(NOW(), 59), 4),
  (SUBDATE(NOW(), 10), 5),
  (SUBDATE(NOW(), 20), 5),
  (SUBDATE(NOW(), 30), 5),
  (SUBDATE(NOW(), 60), 5),
  (SUBDATE(NOW(), 70), 5);

insert into responsable (nombre, edad) values
  ("Pacho Gangotena", 72),
  ("Maritza Rubio", 60),
  ("Andrés Carrasco", 68),
  ("Manuela Pérez", 17),
  ("Carolina Villegas", 25);

insert into huerta.planta_responsable (planta_id,responsable_id) values
  (1, 1),
  (1, 2),
  (1, 4),
  (2, 1),
  (2, 2),
  (2, 3),
  (3, 3),
  (4, 1),
  (4, 2),
  (5, 2),
  (5, 3),
  (6, 1),
  (6, 2),
  (7, 2),
  (7, 3),
  (8, 1),
  (8, 2),
  (8, 3),
  (9, 1),
  (9, 2),
  (9, 3),
  (10, 1),
  (10, 2),
  (10, 4),
  (11, 3),
  (11, 4),
  (11, 5),
  (12, 1),
  (12, 2),
  (12, 3),
  (12, 4),
  (12, 5),
  (13, 1),
  (13, 3),
  (13, 4),
  (13, 5),
  (14, 4),
  (15, 1),
  (15, 5);
```
