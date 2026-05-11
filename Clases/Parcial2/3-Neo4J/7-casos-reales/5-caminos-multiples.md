# Múltiples caminos

```cypher
MATCH p = (a:Persona {nombre: "Ana"})-[:AMIGO_DE*1..3]->(b:Persona)
RETURN b.nombre, count(p) AS caminos
ORDER BY caminos DESC
```

Esto cuenta cuántos caminos existen entre nodos.

# Interpretando múltiples caminos

Más caminos puede significar:

* redundancia en conexiones
* mayor probabilidad de interacción
* mayor resiliencia de la red

Un nodo con muchos caminos no depende de una sola conexión.


