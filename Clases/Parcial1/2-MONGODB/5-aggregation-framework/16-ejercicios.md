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

## Ejercicio 1

Calcular total de cursos por modalidad y ordenarlos descendente

```JS
db.cursos.aggregate([
  {
    $group: {
      _id: "$modalidad",
      totalCursos: { $sum: 1 }
    }
  },
  {
    $sort: { totalCursos: -1 }
  }
])
```

1. `$group`
   * Agrupa por modalidad
   * Cuenta documentos con `$sum: 1`
2. `$sort`
   * Ordena por totalCursos descendente

### Resultado esperado

```JSON
{ "_id": "online", "totalCursos": 3 }
{ "_id": "presencial", "totalCursos": 2 }
```

### Muy importante

Aquí no hay `$match`, por lo tanto:

* No hay uso de índices
* Se procesan todos los documentos
* Es normal y esperado en reportes globales

## Ejercicio 2

Promedio de créditos por nivel, mostrando solo niveles con promedio mayor a 3

Este ejercicio introduce filtrado posterior al agrupamiento.

```JS
db.cursos.aggregate([
  {
    $group: {
      _id: "$nivel",
      promedioCreditos: { $avg: "$creditos" }
    }
  },
  {
    $match: {
      promedioCreditos: { $gt: 3 }
    }
  },
  {
    $sort: { promedioCreditos: -1 }
  }
])
```

### Explicación importante

Aquí el `$match` ocurre después del `$group`.

Esto es equivalente conceptual a:

HAVING promedioCreditos > 3

En SQL.

### Resultado esperado

```JSON
{ "_id": "avanzado", "promedioCreditos": 5 }
{ "_id": "intermedio", "promedioCreditos": 4 }
```

### Muy importante

Este `$match` no puede usar índice, porque:

* Está filtrando un campo generado en el pipeline
* No existe en la colección original

Muy importante remarcar esto.

## Ejercicio 3

Descomponer tecnologías con \$unwind y contar frecuencia

Primero asegurarse de tener documentos con arrays:

```JS
db.cursos.insertOne({
  nombre: "FullStack",
  nivel: "avanzado",
  creditos: 5,
  modalidad: "online",
  tecnologias: ["MongoDB", "NodeJS", "Docker"]
})
```

luego

```JS
db.cursos.aggregate([
  { $unwind: "$tecnologias" },
  {
    $group: {
      _id: "$tecnologias",
      totalUso: { $sum: 1 }
    }
  },
  {
    $sort: { totalUso: -1 }
  }
])
```

### Explicación

1. `$unwind`
   * Convierte cada elemento del array en documento independiente
   * Multiplica temporalmente los documentos
2. `$group`
   * Cuenta frecuencia de cada tecnología

### Resultado esperado

```JSON
{ "_id": "MongoDB", "totalUso": 2 }
{ "_id": "NodeJS", "totalUso": 1 }
{ "_id": "Docker", "totalUso": 1 }
```

### Muy importante

Si el array tiene 50 elementos por documento:

* `$unwind` multiplica enormemente el volumen
* Impacta rendimiento

## Ejercicio 4

Usar \$lookup para mostrar pedidos con nombre del cliente

### Preparación

```JS
use tienda

db.clientes.insertMany([
  { _id: 1, nombre: "Ana", ciudad: "Madrid" },
  { _id: 2, nombre: "Luis", ciudad: "Barcelona" }
])

db.pedidos.insertMany([
  { total: 200, clienteId: 1 },
  { total: 300, clienteId: 2 }
])
```

### Solución

```JS
db.pedidos.aggregate([
  {
    $lookup: {
      from: "clientes",
      localField: "clienteId",
      foreignField: "_id",
      as: "clienteInfo"
    }
  }
])
```

### Resultado esperado

```JSON
{
  "total": 200,
  "clienteId": 1,
  "clienteInfo": [
    { "_id": 1, "nombre": "Ana", "ciudad": "Madrid" }
  ]
}
```

### Mejora

Podemos simplificar con `$unwind`:

```JS
db.pedidos.aggregate([
  {
    $lookup: {
      from: "clientes",
      localField: "clienteId",
      foreignField: "_id",
      as: "clienteInfo"
    }
  },
  { $unwind: "$clienteInfo" },
  {
    $project: {
      total: 1,
      cliente: "$clienteInfo.nombre",
      ciudad: "$clienteInfo.ciudad"
    }
  }
])
```

Ahora el resultado es más limpio.

### Discusión arquitectónica

Si usamos `$lookup` constantemente:

* Tal vez deberíamos denormalizar
* MongoDB favorece documentos enriquecidos

## Ejercicio 5

Reordenar un pipeline incorrecto y medir diferencia con explain()

### Pipeline incorrecto

```JS
db.cursos.aggregate([
  {
    $group: {
      _id: "$nivel",
      total: { $sum: 1 }
    }
  },
  {
    $match: { nivel: "avanzado" }
  }
]).explain("executionStats")
```

### Problema

* `$match` está después del `$group`
* No existe campo nivel en resultado
* Es lógicamente incorrecto

### Versión correcta

```JS
db.cursos.aggregate([
  {
    $match: { nivel: "avanzado" }
  },
  {
    $group: {
      _id: "$nivel",
      total: { $sum: 1 }
    }
  }
]).explain("executionStats")
```

### Qué observar en explain()

* Si existe índice en `nivel`, debería verse IXSCAN
* Menor totalDocsExamined
* Menor tiempo de ejecución

### Lección clave

El orden del pipeline afecta:

* Resultado lógico
* Uso de índices
* Rendimiento

