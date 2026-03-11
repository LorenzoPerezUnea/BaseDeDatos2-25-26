# Índices multikey (arrays)

Documento:

```js
{
  nombre: "Luis",
  habilidades: ["Java", "MongoDB", "Docker"]
}
```

Crear índice:

```js
db.estudiantes.createIndex({ habilidades: 1 })
```

MongoDB crea un índice por cada elemento del array.

Esto se llama:

Multikey Index

Permite consultas como:

```js
db.estudiantes.find({ habilidades: "MongoDB" })
```

