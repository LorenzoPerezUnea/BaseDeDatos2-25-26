# Validación de esquema con JSON Schema

Una de las características más poderosas de MongoDB es su flexibilidad estructural. Sin embargo, esta flexibilidad puede generar inconsistencias si no se controla adecuadamente.

MongoDB permite definir reglas de validación mediante ​JSON Schema​, que actúa como una capa de control estructural sobre los documentos.

Ejemplo de creación de colección con validación:

```JS
db.createCollection("cursos", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["nombre", "nivel", "creditos"],
      properties: {
        nombre: {
          bsonType: "string",
          description: "Debe ser un texto"
        },
        nivel: {
          enum: ["basico", "intermedio", "avanzado"]
        },
        creditos: {
          bsonType: "int",
          minimum: 1,
          maximum: 10
        }
      }
    }
  }
})
```

Esta validación impone reglas claras:

* `nombre` debe ser texto
* `nivel` debe pertenecer a un conjunto específico
* `creditos` debe ser un número entero entre 1 y 10

Si intentamos insertar un documento inválido:

```JS
db.cursos.insertOne({
  nombre: "MongoDB avanzado",
  nivel: "experto",
  creditos: 5
})
```

MongoDB rechazará la operación porque `"experto"` no está definido en el esquema.

