# \$limit — Controlando volumen y propósito analítico

La etapa `$limit` parece simple, pero conceptualmente es muy importante.

Ejemplo:

```JS
db.cursos.aggregate([
  { $sort: { creditos: -1 } },
  { $limit: 3 }
])
```

Aquí estamos respondiendo a una pregunta concreta:

> ¿Cuáles son los tres cursos con mayor cantidad de créditos?

Este tipo de consulta es extremadamente común en:

* Dashboards
* Rankings
* Reportes ejecutivos
* APIs que devuelven “Top N”

### Consideración técnica importante

El orden importa.

Correcto:

```JS
$sort → $limit
```

Incorrecto (semánticamente distinto):

```JS
$limit → $sort
```

Si limitamos primero, solo ordenamos ese subconjunto.

