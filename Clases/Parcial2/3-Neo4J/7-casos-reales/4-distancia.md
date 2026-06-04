# Análisis de distancia

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..4]->(b:Persona)
RETURN a.nombre, b.nombre, length(p) AS distancia
ORDER BY distancia ASC
```

Esto mide qué tan cerca están los nodos.

La distancia en un grafo es información.

# Interpretando distancia

* distancia corta → relación cercana
* distancia larga → conexión débil o indirecta

Pero también:

* muchas distancias cortas → red densa
* pocas → red fragmentada
  

