# JSON como base del modelo documental

Las bases documentales trabajan naturalmente con JSON.
JSON significa JavaScript Object Notation y es un formato ligero para intercambio de datos.

Un documento en MongoDB se parece conceptualmente a un objeto JSON.

Ejemplo simple de JSON:

[simple](json/1-json-simple.json)

Este ejemplo muestra:

- Pares clave valor
- Tipos básicos como texto, número y booleano
- Estructura clara y legible

Ejemplo más complejo:

[complejo](json/2-json-complejo.json)

Aquí observamos:

- Subdocumentos
- Listas
- Estructuras anidadas
- Entidad autocontenida

Este tipo de estructura es difícil de representar en una sola fila relacional sin múltiples tablas y joins.

## Qué es un payload

En el contexto de aplicaciones web y APIs, un payload es el cuerpo de datos que se envía dentro de una petición HTTP.

Cuando un cliente envía datos al servidor, generalmente lo hace en formato JSON. Ese JSON es el payload.

Ejemplo de payload en una petición para crear un usuario:

{
"nombre": "Ana",
"email": "ana@email.com",
"roles": ["editor", "autor"]
}

El servidor recibe este payload y puede almacenarlo directamente como documento en MongoDB.

## Flujo conceptual del payload hasta la base de datos

```mermaid
flowchart LR
    Cliente --> API
    API --> PayloadJSON
    PayloadJSON --> MongoDB
    MongoDB --> Documento
```

