# \$unwind — Desnormalizando arrays para análisis

Uno de los puntos fuertes del modelo documental es que podemos almacenar arrays dentro de documentos.

Ejemplo:

```JS
{
  nombre: "Curso FullStack",
  tecnologias: ["MongoDB", "NodeJS", "Docker"]
}
```

Pero si queremos responder:

> ¿Cuál es la tecnología más utilizada en todos los cursos?

Necesitamos tratar cada elemento del array como una unidad independiente.

Ahí entra `$unwind`.

### Ejemplo práctico

```JS
db.cursos.aggregate([
  { $unwind: "$tecnologias" },
  {
    $group: {
      _id: "$tecnologias",
      total: { $sum: 1 }
    }
  },
  { $sort: { total: -1 } }
])
```

### ¿Qué hace realmente \$unwind?

Convierte:

```JS
{
  nombre: "Curso FullStack",
  tecnologias: ["MongoDB", "NodeJS", "Docker"]
}
```

En:

```JS
{ nombre: "Curso FullStack", tecnologias: "MongoDB" }
{ nombre: "Curso FullStack", tecnologias: "NodeJS" }
{ nombre: "Curso FullStack", tecnologias: "Docker" }
```

Es decir, multiplica documentos temporalmente.

### Advertencia importante

Si el array es grande, `$unwind` puede multiplicar drásticamente el volumen de datos en el pipeline.

Esto impacta:

* Memoria
* CPU
* Tiempo de ejecución

Por eso debemos usarlo con criterio.

