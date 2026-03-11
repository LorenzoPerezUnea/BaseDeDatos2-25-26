# Índices y ordenamiento

Consulta:

```js
db.cursos.find().sort({ creditos: 1 })
```

Si no existe índice en `creditos`:

* MongoDB debe ordenar en memoria
* Puede usar más de 100MB
* Puede fallar si excede límite

Con índice:

```js
db.cursos.createIndex({ creditos: 1 })
```

Ahora el índice ya está ordenado.

MongoDB no necesita ordenar nada adicional.

### Regla importante

Si filtras y ordenas, el orden del índice importa.

Ejemplo:

```js
db.cursos.find({ profesor: "Dr. Pérez" }).sort({ creditos: 1 })
```

Índice ideal:

```js
db.cursos.createIndex({ profesor: 1, creditos: 1 })
```

Primero filtro, luego orden.

