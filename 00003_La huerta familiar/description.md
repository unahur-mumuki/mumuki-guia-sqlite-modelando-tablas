<div
  class='mu-erd'
  data-entities='{
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
      "toleraSombra": {
        "type": "Boolean"
      },
      "id_origen": { 
        "type": "Integer",
        "fk": {
          "to": { "entity": "origen", "column": "id" },
          "type": "many_to_one"
        }
      }
    },
    "origen": {
      "id": {
        "type": "Integer",
        "pk": true
      },
      "nombre": {
         "type": "Text"
      },
      "latitud": {
        "type": "Integer"
      },
      "longitud": {
        "type": "Integer"
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
      "fechaSiembra": {
        "type": "Date"
      },
      "semilla_id": {
        "fk": {
          "to": { "entity": "semilla", "column": "id" },
          "type": "many_to_one"
        }
      }
    }
  }'>
</div>