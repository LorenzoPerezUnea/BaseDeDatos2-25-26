# Sintaxis básica y estructura general

La estructura general es:

```JS
db.coleccion.aggregate([
   { etapa1 },
   { etapa2 },
   { etapa3 }
])
```

Es un arreglo ordenado.

Esto significa que estamos declarando una secuencia de transformaciones.

Ejemplo mínimo:

```JS
db.cursos.aggregate([
   { $match: { modalidad: "online" } }
])
```

Este pipeline tiene una sola etapa.

Pero incluso en este caso ya estamos usando el motor de agregación, no el motor simple de búsqueda.

