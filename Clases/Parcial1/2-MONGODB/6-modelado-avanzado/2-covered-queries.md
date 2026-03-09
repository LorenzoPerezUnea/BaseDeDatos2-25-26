# Covered Queries — Consultas resueltas solo con índice

Una Covered Query ocurre cuando MongoDB puede responder la consulta usando únicamente el índice, sin acceder al documento original.

Esto es extremadamente eficiente.

### Ejemplo

Crear índice:

```JS
db.cursos.createIndex({ nivel: 1, creditos: 1 })
```

Consulta:

```JS
db.cursos.find(
  { nivel: "avanzado" },
  { nivel: 1, creditos: 1, _id: 0 }
).explain("executionStats")
```

Si todo está correctamente alineado:

* totalDocsExamined = 0
* totalKeysExamined > 0
* No hay FETCH stage

Esto significa que MongoDB nunca tocó la colección.

### ¿Por qué es tan eficiente?

Porque el índice contiene:

nivel + creditos + referencia

Y estamos solicitando exactamente esos campos.

### Regla fundamental

Para que exista Covered Query:

1. Todos los campos filtrados deben estar en el índice.
2. Todos los campos proyectados deben estar en el índice.
3. Debemos excluir `_id` si no está en el índice.

Este es un concepto avanzado y muy valioso en sistemas de alto rendimiento.

