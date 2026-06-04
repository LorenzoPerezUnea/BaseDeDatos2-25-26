# Cuando el grafo deja de ser datos y se convierte en información

Hasta ahora has construido consultas que devuelven resultados.

Personas, empresas, proyectos, conexiones.

Pero en esta clase vamos a cambiar la forma de mirar el resultado.

Un grafo no solo responde preguntas.

Un grafo permite descubrir cosas que no sabías que existían.

Eso es análisis.

### De consultas a interpretación

Observa esta consulta:

```cypher
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN e.nombre, count(p)
ORDER BY count(p) DESC
```

Esto devuelve empresas con más empleados.

Pero la consulta no es lo importante.

La pregunta es:

¿qué significa que una empresa tenga más conexiones?

Puede significar:

* mayor tamaño
* mayor centralidad
* mayor influencia en el grafo

El dato es el mismo.

La interpretación cambia.



