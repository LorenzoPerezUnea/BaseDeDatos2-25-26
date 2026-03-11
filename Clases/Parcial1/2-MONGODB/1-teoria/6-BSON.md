# Relación entre JSON y BSON

MongoDB almacena documentos en formato BSON.

BSON es una representación binaria de JSON que:

* Agrega tipos de datos adicionales
* Mejora eficiencia
* Permite fechas y datos binarios

Conceptualmente el desarrollador trabaja con JSON, pero el motor almacena BSON.

## Ejemplo conceptual de documento en MongoDB

Documento usuario:

{
"\_id": "abc123",
"nombre": "Laura",
"edad": 30,
"roles": ["admin", "editor"]
}

El campo _id es obligatorio y actúa como identificador único del documento.

