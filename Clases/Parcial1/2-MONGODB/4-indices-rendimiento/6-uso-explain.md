# explain()

Permite analizar cómo se ejecuta una consulta:

```js
db.cursos.find({ nivel: "Avanzado" }).explain("executionStats")
```

Conceptos:

* COLLSCAN
* IXSCAN
* totalDocsExamined
* totalKeysExamined

### COLLSCAN

Indica que MongoDB recorrió toda la colección.

Ejemplo:

```js
"stage": "COLLSCAN"
```

Es una alerta roja en producción.

### IXSCAN

Indica uso de índice.

```js
"stage": "IXSCAN"
```

Es lo que queremos ver en consultas frecuentes.

### totalDocsExamined

Número de documentos que MongoDB realmente evaluó.

Si tienes 1 millón de documentos y ves:

```js
"totalDocsExamined": 1000000
```

Es un problema.

Idealmente:

```js
"totalDocsExamined": 3
```

### totalKeysExamined

Número de entradas del índice evaluadas.

Ejemplo ideal:

```js
"totalKeysExamined": 3
"totalDocsExamined": 3
```

Eso indica eficiencia.

### Demostración práctica paso a paso

Sin índice:

```js
db.cursos.find({ nivel: "Avanzado" }).explain("executionStats")
```

Observar:

* stage: COLLSCAN
* totalDocsExamined alto

```js
"stage": "COLLSCAN",
"totalDocsExamined": 1000000
```

Crear índice:

```js
db.cursos.createIndex({ nivel: 1 })
```

Repetir explain.

Ahora debería mostrar:

* stage: IXSCAN
* totalDocsExamined reducido

```js
"stage": "IXSCAN",
"totalDocsExamined": 3,
"totalKeysExamined": 3
```

