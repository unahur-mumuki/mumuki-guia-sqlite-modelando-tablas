<div
  class='mu-erd'
  data-entities='{
    "origen": {
      "id": {
        "type": "Integer",
        "pk": true
      },
      "nombre": {
         "type": "Text"
      },
      "pais": {
        "type": "Text"
      }
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
      "nombre": {
        "type": "Text"
      },
      "anio": {
        "type": "Integer"
      },
      "tolera_sombra": {
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
      "fecha_siembra": {
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
      "nombre": {
        "type": "Text"
      },
      "edad": {
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

**Valores por defecto**:

* Fecha 21/09/2019 en `fecha_siembra` de Planta.
* Edad 18 en Responsable.

**Consultas**:

* Responsables menores de 18 años de las plantas de cualquier variedad de cacao. Pista: el nombre de la semilla tiene que contener el texto "cacao".
* Plantas que no toleran sombra, sembradas en los ultimos 6 meses.
* Nombre y origen de las tres semillas más utilizadas (o sea, las que más plantas tienen).
