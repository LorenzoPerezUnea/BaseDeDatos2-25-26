# Principios de modelado documental avanzado

Hasta ahora hemos trabajado con colecciones como `cursos`, `estudiantes` y `pedidos`, pero aún no hemos profundizado en la pregunta más importante en MongoDB:

> ¿Cómo debo diseñar mis documentos desde el inicio?

En bases relacionales el diseño parte de la normalización.
En MongoDB el diseño parte del patrón de consulta.

Este cambio de mentalidad es fundamental.

### Diseño basado en acceso, no en estructura

En MongoDB debemos preguntarnos:

* ¿Cómo se va a consultar la información?
* ¿Qué datos suelen recuperarse juntos?
* ¿Qué operaciones deben ser atómicas?

La respuesta a estas preguntas determina si usamos:

* Embedding (documentos embebidos)
* Referencing (referencias entre colecciones)

### Embedding (Incrustación)

Ejemplo:

```JS
{
  _id: 1,
  cliente: {
    nombre: "Ana",
    ciudad: "Madrid"
  },
  productos: [
    { nombre: "Libro", precio: 20 }
  ]
}
```

Ventajas:

* Lecturas rápidas (todo en un solo documento)
* Atomicidad natural
* Menos joins (\$lookup)

Desventajas:

* Crecimiento del documento
* Duplicación de datos
* Límites de tamaño (16 MB)

### Referencing (Referencias)

Ejemplo:

```JS
pedido: { clienteId: ObjectId(...) }
```

Ventajas:

* No duplicación
* Documentos más pequeños
* Flexibilidad

Desventajas:

* Requiere \$lookup
* Más complejidad
* Más costo de consulta

### Regla profesional

Embed cuando:

* Los datos se leen juntos
* La relación es uno-a-pocos
* El crecimiento está controlado

Referencia cuando:

* La relación es muchos-a-muchos
* Los datos cambian frecuentemente
* El tamaño puede crecer sin límite
  

