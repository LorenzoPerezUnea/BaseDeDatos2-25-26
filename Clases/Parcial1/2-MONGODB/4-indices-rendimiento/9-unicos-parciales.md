# Índices únicos y parciales

### Índices únicos

Evitan duplicados.

```js
db.usuarios.createIndex(
  { email: 1 },
  { unique: true }
)
```

Si intentas insertar:

```js
{ email: "test@mail.com" }
```

Dos veces → error.

### Índices únicos y consistencia

```js
db.cursos.createIndex(
  { nombre: 1 },
  { unique: true }
)
```

Si intentamos insertar duplicado:

MongoDB lanzará error.

Esto introduce control de integridad similar a SQL.

Muy útil para:

* Emails
* DNI
* Códigos únicos

### Índices parciales

Indexan solo documentos que cumplen condición.

Ejemplo:

```js
db.pedidos.createIndex(
  { estado: 1 },
  { partialFilterExpression: { estado: "activo" } }
)
```

Ventaja:

* Índice más pequeño
* Menor uso de memoria
* Mejor rendimiento

Ideal cuando:

* 90% de documentos están inactivos
* Solo consultas activos

Reduce tamaño del índice.

