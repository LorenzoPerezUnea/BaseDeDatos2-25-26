# Consideraciones de memoria y allowDiskUse

Cuando agrupamos grandes volúmenes:

* `$group` mantiene estructuras en memoria
* `$sort` puede requerir buffers grandes

MongoDB tiene límites internos.

Si se exceden:

```JS
db.cursos.aggregate(pipeline, { allowDiskUse: true })
```

Esto permite usar disco temporalmente.

En producción, esto debe monitorearse.

