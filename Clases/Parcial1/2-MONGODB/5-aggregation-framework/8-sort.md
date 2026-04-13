# \$sort — Ordenamiento dentro del pipeline

Ordena los resultados intermedios.

Ejemplo:

```JS
db.cursos.aggregate([
  {
    $group: {
      _id: "$nivel",
      total: { $sum: 1 }
    }
  },
  { $sort: { total: -1 } }
])
```

Aspecto importante:

Si el ordenamiento ocurre después de `$group`, ya no puede usar índice original.

Porque estamos ordenando resultados transformados.

Esto es clave para análisis de rendimiento.

### Consideración de memoria

Si el volumen es grande:

* `$sort` puede usar memoria significativa
* MongoDB tiene límites internos
* Puede requerir `allowDiskUse: true`

Ejemplo:

```JS
db.cursos.aggregate(pipeline, { allowDiskUse: true })
```

Este tipo de detalle es importante en sistemas reales.

