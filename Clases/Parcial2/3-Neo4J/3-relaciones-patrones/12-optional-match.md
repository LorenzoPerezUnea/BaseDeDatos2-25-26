# Introduciendo OPTIONAL MATCH

Ahora vamos a ver algo muy importante.

```cypher
MATCH (a:Persona)
OPTIONAL MATCH (a)-[:PARTICIPA_EN]->(p:Proyecto)
RETURN a, p
```

Ejecuta.

Esto incluye personas sin proyecto.

En SQL sería como un LEFT JOIN.

Mira los resultados.

¿qué pasa con los nodos sin relaciones?

b aparece como null.

Esto es fundamental para no perder información.

### Variación con filtro

```cypher
MATCH (a:Persona)
OPTIONAL MATCH (a)-[:PARTICIPA_EN]->(p:Proyecto)
WHERE p.presupuesto > 60000
RETURN a, p
```

Ejecuta.

Observa qué ocurre.

Este tipo de combinaciones puede dar resultados inesperados si no se entiende bien.

