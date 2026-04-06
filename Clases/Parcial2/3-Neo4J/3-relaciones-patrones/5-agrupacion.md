# Introduciendo GROUP BY implícito

En Cypher no escribes GROUP BY como en SQL, pero existe.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a.nombre, count(b)
```

Lo que está pasando es que se agrupa por a.nombre.

Ahora observa esto con calma.

Cada fila representa una persona y el número de amigos que tiene.

### Variación: cambiando la agrupación

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (a)-[:VIVE_EN]->(c:Ciudad)
RETURN c.nombre, count(a)
```

Ejecuta.

Ahora estás contando cuántas personas apuntan a cada nodo.

Este tipo de cambio es muy potente.

