# \$match — Filtrado dentro del pipeline

`$match` es equivalente conceptual a `find()`, pero integrado en el pipeline.

Ejemplo:

```JS
db.cursos.aggregate([
  { $match: { modalidad: "online" } }
])
```

Ahora bien, aquí es donde empieza la parte técnica interesante.

Si existe un índice en `modalidad`, MongoDB puede utilizarlo incluso dentro del pipeline.

Por eso es buena práctica colocar `$match` lo más temprano posible.

### ¿Por qué?

Porque reduce el volumen de datos que fluye hacia las siguientes etapas.

Si no filtramos temprano:

* `$group` procesará más datos
* `$sort` ordenará más datos
* Se consumirá más memoria

En sistemas reales, el orden correcto del pipeline puede marcar una diferencia enorme en rendimiento.

