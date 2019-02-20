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
        "pk": true,
      }
    }
  }'>
</div>