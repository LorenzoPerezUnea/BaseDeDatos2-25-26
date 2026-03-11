# Ejercicios Avanzados 2

# Ejercicio 5

### Índice único

### Crear índice

```js
use universidad

db.cursos.createIndex(
  { nombre: 1 },
  { unique: true }
)
```

### Intentar insertar duplicado

```js
db.cursos.insertOne({
  nombre: "MongoDB Básico",
  nivel: "básico",
  creditos: 3
})
```

### Resultado esperado

Error:

duplicate key error

### Interpretación

MongoDB protege la integridad lógica del dato.

## Ejercicio 6

### Índice parcial

### Crear índice

```js
db.cursos.createIndex(
  { modalidad: 1 },
  { partialFilterExpression: { modalidad: "online" } }
)
```

### Ver índices

```js
db.cursos.getIndexes()
```

### Interpretación

El índice solo contiene documentos donde modalidad = online.

Ventajas:

* Menor tamaño
* Mejor uso de memoria
* Mejor rendimiento selectivo

## Ejercicio 7

### Baja cardinalidad

Campo candidato:

```js
modalidad: "online" o "presencial"
```

Solo 2 valores.

### Debate técnico

Si ejecutas:

```js
db.cursos.find({ modalidad: "online" }).explain("executionStats")
```

Probablemente:

* totalDocsExamined alto
* Poco beneficio del índice

### Conclusión conceptual

Campos con pocos valores distintos suelen no ser buenos candidatos para indexación aislada.

## Ejercicio 8

### Eliminar índice

```js
db.cursos.dropIndex({ nivel: 1 })
```

### Verificar

```js
db.cursos.getIndexes()
```

