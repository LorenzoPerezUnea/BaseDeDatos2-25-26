# Pensando en consultas más ricas

Haz una pausa.

Ahora puedes:

* diferenciar relaciones
* añadir propiedades
* filtrar por ellas

Esto te permite modelar cosas mucho más cercanas a la realidad.

### Introduciendo relaciones bidireccionales conceptuales

Hasta ahora has trabajado con dirección.

Pero hay relaciones que conceptualmente son simétricas.

```cypher
MATCH (a)-[:AMIGO_DE]-(b)
MATCH (a)-[:VIVE_EN]->(c:Ciudad)
RETURN a, b, c
```

Ejecuta.

Esto ignora la dirección.

### Variación: combinando con filtros

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]-(b:Persona)
MATCH (a)-[:VIVE_EN]->(c:Ciudad)
WHERE 
  a.edad >= 30 AND 
  b.edad >= 28 AND 
  r.intensidad >= 7 AND 
  r.desde <= 2020 AND
  c.nombre IN ["Madrid", "Barcelona"]
RETURN 
  a,
  b,
  c,
  r
```

o mejor:

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]-(b:Persona)
MATCH (a)-[:VIVE_EN]->(c:Ciudad)
WHERE 
  a.edad >= 30 AND 
  b.edad >= 28 AND 
  r.intensidad >= 7 AND 
  r.desde <= 2020 AND
  c.nombre IN ["Madrid", "Barcelona"]
RETURN 
  a.nombre AS persona,
  b.nombre AS amigo,
  c.nombre AS ciudad,
  r.intensidad,
  r.desde
ORDER BY r.intensidad DESC, persona
```

Observa cómo cambia el resultado.

