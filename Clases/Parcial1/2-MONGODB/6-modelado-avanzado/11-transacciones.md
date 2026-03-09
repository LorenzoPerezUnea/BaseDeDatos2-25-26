# Transacciones en MongoDB

MongoDB soporta transacciones multi-documento.

Pero debemos entender su costo.

MongoDB no fue diseñado originalmente para depender de transacciones extensivas como en sistemas relacionales.

La filosofía documental intenta evitar la necesidad de transacciones complejas mediante buen modelado (embedding).

### ¿Cuándo usarlas?

* Cuando se requiere atomicidad estricta
* Cuando múltiples documentos deben modificarse juntos

### ¿Cuándo evitarlas?

* Operaciones simples
* Casos donde embedding resuelve atomicidad

Transacciones:

* Aumentan latencia
* Reducen rendimiento bajo alta carga

En MongoDB, primero diseñamos para evitar transacciones.

Ejemplo de transacción:

```JS
session = db.getMongo().startSession()
session.startTransaction()

try {
  session.getDatabase("academia").cursos.insertOne({ nombre: "Nuevo" })
  session.getDatabase("academia").estudiantes.updateOne(
    { nombre: "Ana" },
    { $set: { activo: true } }
  )
  session.commitTransaction()
} catch (e) {
  session.abortTransaction()
}
```

Costos de transacciones:

* Mayor consumo de memoria.
* Bloqueos más prolongados.
* Mayor latencia.
* Menor throughput bajo alta concurrencia.

Conclusión profesional:

Usar transacciones cuando son necesarias.
Pero diseñar para no depender de ellas.

Embedding muchas veces elimina la necesidad.

