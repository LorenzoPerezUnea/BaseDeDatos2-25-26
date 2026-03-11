# Índices en campos embebidos

Documento:

```js
{
  nombre: "Ana",
  direccion: {
    ciudad: "Madrid",
    codigoPostal: "28001"
  }
}
```

Crear índice:

```js
db.estudiantes.createIndex({ "direccion.ciudad": 1 })
```

MongoDB indexa el campo interno.

Consulta:

```js
db.estudiantes.find({ "direccion.ciudad": "Madrid" })
```

Usará IXSCAN si el índice existe.

