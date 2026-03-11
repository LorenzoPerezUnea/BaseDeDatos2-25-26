# Creación de índice

### Índices simples

```js
db.cursos.createIndex({ nombre: 1 })
```

1 indica orden ascendente
-1 indica descendente

Par ver índices creados:

```js
db.cursos.getIndexes()
```

### Índices compuestos

```js
db.cursos.createIndex({ nivel: 1, creditos: -1 })
```

El orden importa (ascendente o descendente).

