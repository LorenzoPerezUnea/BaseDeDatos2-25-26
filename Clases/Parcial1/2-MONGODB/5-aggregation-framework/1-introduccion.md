# ¿Por qué necesitamos Aggregation Framework?

Hasta ahora hemos trabajado con consultas del tipo:

```JS
db.cursos.find({ nivel: "avanzado" })
```

Este tipo de consulta responde una pregunta binaria:

> ¿Qué documentos cumplen esta condición?

Pero en sistemas reales, esa no es la pregunta más frecuente.

Las preguntas reales suelen ser:

* ¿Cuántos cursos hay por nivel?
* ¿Cuál es el promedio de créditos por modalidad?
* ¿Qué porcentaje de cursos son online?
* ¿Cuál es el total acumulado por categoría?
* ¿Cuáles son los tres niveles con mayor número de cursos?

Aquí ya no estamos buscando documentos individuales.
Estamos buscando ​**información derivada**​.

En bases de datos relacionales, esto se resuelve con `GROUP BY`, funciones agregadas y subconsultas.

En MongoDB, la respuesta es el ​**Aggregation Framework**​.

### Cambio conceptual importante

Con `find()` hacemos filtrado.

Con `aggregate()` hacemos procesamiento de datos.

Es decir:

CRUD → recuperación directa
Aggregation → transformación estructural

Y este cambio es fundamental porque nos obliga a dejar de pensar en “documentos aislados” y comenzar a pensar en “flujo de datos”.

