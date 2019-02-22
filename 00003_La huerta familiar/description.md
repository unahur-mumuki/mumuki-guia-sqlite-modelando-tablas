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
        "type": "Integer"
      },
      "longitud": {
        "type": "Integer"
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

**Valores por defecto**:

* Fecha 21/09/2019 en `fecha_siembra` de Planta.
* Edad 18 en Responsable.

**Consultas**:

* Nombre y edad de los y las responsables menores de 18 años de las plantas de cualquier variedad de cacao. Pista: el nombre de la semilla tiene que contener el texto "cacao".
* Plantas que no toleran sombra, sembradas en los ultimos 6 meses. Mostrar el nombre de la planta, el país de origen y la fecha de siembra.
* Nombre y lugar de origen de las tres semillas más utilizadas (o sea, las que más plantas tienen).
