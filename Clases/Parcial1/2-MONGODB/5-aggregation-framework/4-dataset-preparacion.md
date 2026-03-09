# Dataset de trabajo y preparación

Trabajaremos sobre la colección `cursos`:

```JS
use universidad
```

Ejemplo de documentos:

```JS
db.cursos.insertMany([
  { nombre: "MongoDB Básico", nivel: "básico", creditos: 3, modalidad: "online" },
  { nombre: "MongoDB Intermedio", nivel: "intermedio", creditos: 4, modalidad: "presencial" },
  { nombre: "MongoDB Avanzado", nivel: "avanzado", creditos: 5, modalidad: "online" },
  { nombre: "NodeJS Básico", nivel: "básico", creditos: 3, modalidad: "presencial" },
  { nombre: "Docker Básico", nivel: "básico", creditos: 2, modalidad: "online" }
])
```

Antes de seguir, es importante que los estudiantes entiendan algo:

Aggregation no crea tablas nuevas.
Aggregation no modifica datos.
Aggregation genera resultados temporales.

Estamos construyendo vistas dinámicas.

