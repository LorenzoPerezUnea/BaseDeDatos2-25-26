# Ejercicios

## BD academia

```JS
use academia

db.cursos.drop()
db.estudiantes.drop()
db.inscripciones.drop()
```

### cursos

```JS
const niveles = ["basico", "intermedio", "avanzado"]
const modalidades = ["online", "presencial", "hibrido"]

for (let i = 1; i <= 50; i++) {
  db.cursos.insertOne({
    nombre: "Curso " + i,
    descripcion: "Curso completo de bases de datos y MongoDB nivel " + niveles[i % 3],
    nivel: niveles[i % 3],
    modalidad: modalidades[i % 3],
    creditos: (i % 5) + 1,
    fechaCreacion: new Date(2024, i % 12, (i % 28) + 1),
    fechaCertificacion: i % 4 === 0 ? new Date(2025, i % 12, (i % 28) + 1) : null
  })
}
```

para Sparse

```JS
db.cursos.deleteMany({ fechaCertificacion: null })

for (let i = 1; i <= 50; i++) {
  db.cursos.insertOne({
    nombre: "Curso Extra " + i,
    descripcion: "Programa avanzado de optimizacion y modelado documental",
    nivel: niveles[i % 3],
    modalidad: modalidades[i % 3],
    creditos: (i % 5) + 1,
    fechaCreacion: new Date(2024, i % 12, (i % 28) + 1),
    ...(i % 3 === 0 && { fechaCertificacion: new Date(2025, i % 12, (i % 28) + 1) })
  })
}
```

### estudiantes

```JS
for (let i = 1; i <= 60; i++) {
  db.estudiantes.insertOne({
    nombre: "Estudiante " + i,
    email: "estudiante" + i + "@correo.com",
    edad: 18 + (i % 10),
    ciudad: ["Madrid", "Bogota", "CDMX", "Buenos Aires"][i % 4],
    activo: i % 2 === 0,
    telefonoAlternativo: i % 5 === 0 ? "600000" + i : undefined
  })
}
```

### inscripciones

```JS
for (let i = 1; i <= 100; i++) {
  db.inscripciones.insertOne({
    estudianteId: (i % 60) + 1,
    cursoId: (i % 50) + 1,
    fecha: new Date(2025, i % 12, (i % 28) + 1),
    estado: ["activa", "completada", "cancelada"][i % 3],
    nota: Math.floor(Math.random() * 5) + 1
  })
}
```

## BD tienda

```JS
use tienda

db.pedidos.drop()
db.ventas.drop()
db.logs.drop()
```

### pedidos

```JS
for (let i = 1; i <= 100; i++) {
  db.pedidos.insertOne({
    clienteId: (i % 30) + 1,
    fecha: new Date(2026, i % 12, (i % 28) + 1),
    total: Math.floor(Math.random() * 1000) + 50,
    estado: ["pendiente", "enviado", "entregado"][i % 3],
    cliente: {
      nombre: "Cliente " + ((i % 30) + 1),
      ciudad: ["Madrid", "Lima", "CDMX", "Santiago"][i % 4]
    }
  })
}
```

### ventas

```JS
for (let i = 1; i <= 80; i++) {
  db.ventas.insertOne({
    clienteId: (i % 25) + 1,
    producto: "Producto " + (i % 15),
    cantidad: (i % 5) + 1,
    total: Math.floor(Math.random() * 500) + 20,
    fecha: new Date(2026, i % 12, (i % 28) + 1)
  })
}
```

### logs

```JS
for (let i = 1; i <= 100; i++) {
  db.logs.insertOne({
    usuarioId: (i % 20) + 1,
    accion: ["login", "logout", "compra", "consulta"][i % 4],
    fecha: new Date(Date.now() - (i * 1000000))
  })
}
```

## Ejercicio 1 — Sparse Index

1. Crear colección usuarios con algunos documentos que tengan campo telefonoAlternativo.
2. Crear índice normal sobre telefonoAlternativo.
3. Crear índice sparse.
4. Comparar getIndexes().
5. Ejecutar consultas con explain().

```JS
use academia

db.usuarios.drop()
db.usuarios.insertMany([
  { nombre: "Ana", telefonoAlternativo: "1111" },
  { nombre: "Luis" },
  { nombre: "Carlos", telefonoAlternativo: "2222" },
  { nombre: "Marta" },
  { nombre: "Elena", telefonoAlternativo: "3333" }
])

db.usuarios.createIndex({ telefonoAlternativo: 1 })

db.usuarios.getIndexes()

db.usuarios.dropIndex({ telefonoAlternativo: 1 })

db.usuarios.createIndex(
  { telefonoAlternativo: 1 },
  { sparse: true }
)

db.usuarios.getIndexes()

db.usuarios.find(
  { telefonoAlternativo: { $exists: true } }
).explain("executionStats")
```

Preguntas:

* ¿Cuántos documentos indexa cada uno?
* ¿Cuál es el tamaño del índice?

## Ejercicio 2 — Hashed Index

1. Crear colección ventas con campo clienteId.
2. Crear índice hashed.
3. Ejecutar consulta exacta.
4. Intentar consulta por rango.

```JS
use tienda

db.ventas.drop()
db.ventas.insertMany([
  { clienteId: 1001, total: 200 },
  { clienteId: 1002, total: 150 },
  { clienteId: 1003, total: 300 },
  { clienteId: 1004, total: 120 },
  { clienteId: 1005, total: 450 }
])

db.ventas.createIndex({ clienteId: "hashed" })

db.ventas.getIndexes()

db.ventas.find({ clienteId: 1003 }).explain("executionStats")

db.ventas.find({ clienteId: { $gt: 1002 } }).explain("executionStats")
```

Reflexión:
¿Por qué el índice no sirve para rango?

## Ejercicio 3 — Simulación conceptual de shard key

Dado un sistema de pedidos:

* 90% consultas por clienteId.
* 10% reportes por fecha.

```JS
use tienda

sh.enableSharding("tienda")

sh.shardCollection("tienda.pedidos", { clienteId: 1 })

db.pedidos.insertMany([
  { clienteId: 1001, total: 200 },
  { clienteId: 1500, total: 300 },
  { clienteId: 2200, total: 500 },
  { clienteId: 2700, total: 100 }
])

db.pedidos.find({ clienteId: 1500 })

db.pedidos.find({ total: { $gt: 100 } })
```

¿Cuál shard key elegirías y por qué?

## Ejercicio 4 — Transacciones

1. Ejecutar dos inserts sin transacción.
2. Simular error intermedio.
3. Repetir con transacción.
4. Observar diferencia.

```JS
session = db.getMongo().startSession()

dbTx = session.getDatabase("academia")

session.startTransaction()

try {

  dbTx.estudiantes.updateOne(
    { nombre: "Estudiante 1" },
    { $set: { activo: true} }
  )

  dbTx.cursos.insertOne({
    nombre: "Curso 1000"
  })

  print("COMMIT EJECUTADO")

  session.commitTransaction()



} catch(e){

  print("ROLLBACK EJECUTADO")

  session.abortTransaction()

}

session.endSession()
```

```JS
session = db.getMongo().startSession()

dbTx = session.getDatabase("academia")

session.startTransaction()

try {

  dbTx.estudiantes.updateOne(
    { nombre: "Estudiante 1" },
    { $set: { activo: false} }
  )

  dbTx.cursos.insertOne({
    nombre: "Curso 1000"
  })

  print("COMMIT EJECUTADO")

  session.commitTransaction()



} catch(e){

  print("ROLLBACK EJECUTADO")

  session.abortTransaction()

}

session.endSession()
```

```JS
db.estudiantes.find({nombre:  "Estudiante 1" })
```

```JS
db.cursos.find({nombre:  "Curso 1000" })
```

```JS
db.cursos.createIndex({nombre:  1 }, {unique: true})
```

## Ejercicio 5 — Monitoreo

Ejecutar múltiples consultas complejas.
Usar explain().
Identificar:

* COLLSCAN
* totalDocsExamined
* executionTimeMillis

```JS
use academia

db.cursos.find({ nivel: "avanzado" }).explain("executionStats")

db.cursos.find({ creditos: { $gt: 3 } }).explain("executionStats")

db.serverStatus()

db.currentOp()
```

