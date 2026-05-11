# Ejercicio guiado

Construye una consulta que:

* incluya personas sin amigos
* cuente relaciones
* filtre resultados
* ordene

Pista base:

```cypher
MATCH (a:Persona)
OPTIONAL MATCH (a)-[:AMIGO_DE]->(b)
WITH a, count(b) AS amigos
MATCH (a)-[:TRABAJA_EN]->(e)
RETURN a.nombre, e.nombre, amigos
ORDER BY amigos DESC
```

Modifica y prueba.

