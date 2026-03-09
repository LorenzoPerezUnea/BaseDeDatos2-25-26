# explain() en Aggregation

Así como analizamos consultas simples con `explain()`, también podemos hacerlo con agregaciones.

```JS
db.cursos.aggregate([
  { $match: { nivel: "avanzado" } },
  { $group: { _id: "$nivel", total: { $sum: 1 } } }
]).explain("executionStats")
```

### Qué debemos observar

* ¿Se utilizó índice en \$match?
* ¿Aparece COLLSCAN?
* ¿Cuántos documentos fueron examinados?
* ¿Cuánta memoria se usó?

Si `$match` está primero y hay índice, debería verse `IXSCAN`.

Si `$match` está después de `$group`, el índice ya no puede utilizarse.

Este detalle es clave para evaluación.

