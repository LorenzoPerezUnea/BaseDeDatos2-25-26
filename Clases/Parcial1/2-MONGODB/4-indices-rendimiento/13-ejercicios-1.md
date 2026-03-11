# Ejercicios Avanzados 1

## BD inicial

```js
use universidad
```

```js
db.cursos.insertMany([
  { nombre: "MongoDB Básico", nivel: "básico", creditos: 3, modalidad: "online" },
  { nombre: "MongoDB Intermedio", nivel: "intermedio", creditos: 4, modalidad: "presencial" },
  { nombre: "MongoDB Avanzado", nivel: "avanzado", creditos: 5, modalidad: "online" },
  { nombre: "NodeJS Básico", nivel: "básico", creditos: 3, modalidad: "presencial" },
  { nombre: "NodeJS Avanzado", nivel: "avanzado", creditos: 5, modalidad: "online" },
  { nombre: "Docker Básico", nivel: "básico", creditos: 2, modalidad: "online" },
  { nombre: "Docker Intermedio", nivel: "intermedio", creditos: 4, modalidad: "presencial" },
  { nombre: "Kubernetes", nivel: "avanzado", creditos: 5, modalidad: "presencial" },
  { nombre: "SQL Básico", nivel: "básico", creditos: 3, modalidad: "online" },
  { nombre: "SQL Avanzado", nivel: "avanzado", creditos: 5, modalidad: "presencial" }
])
```

## Ejercicio 1

### Medir rendimiento antes y después de crear índice

### Objetivo

Comprender empíricamente la diferencia entre COLLSCAN e IXSCAN.

### Paso 1: Ejecutar consulta sin índice

```js
db.cursos.find({ nivel: "avanzado" }).explain("executionStats")
```

### Qué observar

* "stage": "COLLSCAN"
* totalDocsExamined ≈ total documentos de la colección
* totalKeysExamined: 0

### Interpretación

MongoDB está leyendo todos los documentos para encontrar coincidencias.

### Paso 2: Crear índice

```js
db.cursos.createIndex({ nivel: 1 })
```

### Paso 3: Ejecutar nuevamente

```js
db.cursos.find({ nivel: "avanzado" }).explain("executionStats")
```

### Qué debería cambiar

* "stage": "IXSCAN"
* totalDocsExamined reducido
* totalKeysExamined > 0

### Conclusión esperada

Se demuestra cómo el índice reduce el trabajo necesario para resolver la consulta.

## Ejercicio 2

### Índice compuesto nivel + creditos

### Objetivo

Entender el impacto del orden en índices compuestos.

### Crear índice

```js
db.cursos.createIndex({ nivel: 1, creditos: 1 })
```

### Consulta

```js
db.cursos.find({ nivel: "avanzado" }).sort({ creditos: 1 }).explain("executionStats")
```

### Interpretación esperada

MongoDB debería:

* Usar IXSCAN
* No hacer SORT en memoria
* Reducir totalDocsExamined

### Explicación conceptual

El índice ya está ordenado primero por nivel, luego por creditos.

Esto permite:

Filtro eficiente + Ordenamiento eficiente

## Ejercicio 3

### Consulta solo por creditos

### Ejecutar

```js
db.cursos.find({ creditos: 5 }).explain("executionStats")
```

### Posible resultado

Puede aparecer:

* COLLSCAN
  o
* Uso parcial del índice

### Explicación técnica

El índice es:

```js
{ nivel: 1, creditos: 1 }
```

Regla: MongoDB usa índices compuestos desde el primer campo hacia la derecha.

Si no filtras por nivel, puede no usar el índice eficientemente.

### Conclusión conceptual

El orden del índice debe reflejar los patrones reales de consulta.

## Ejercicio 4

### Índice en campo embebido

Primero crear colección pedidos:

```js
use tienda

db.pedidos.insertMany([
  { total: 100, cliente: { nombre: "Ana", ciudad: "Madrid" } },
  { total: 200, cliente: { nombre: "Luis", ciudad: "Barcelona" } },
  { total: 150, cliente: { nombre: "Pedro", ciudad: "Madrid" } }
])
```

### Crear índice

```js
db.pedidos.createIndex({ "cliente.ciudad": 1 })
```

### Ejecutar consulta

```js
db.pedidos.find({ "cliente.ciudad": "Madrid" }).explain("executionStats")
```

### Interpretación

Debe aparecer:

* IXSCAN
* totalDocsExamined reducido

### Conclusión

MongoDB indexa campos embebidos usando notación punto.

