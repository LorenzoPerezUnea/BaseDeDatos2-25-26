# Introduciendo tipos de relaciones múltiples

Antes solo has usado AMIGO\_DE entre otras relaciones.

Vamos a añadir otro tipo.

```cypher
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa)
MATCH (e)-[:GESTIONA]->(pr:Proyecto)
RETURN p, pr
```

Consulta:

```cypher
MATCH (a)-[r]->(b)
RETURN a, r, b
```

Ahora tienes distintos tipos de relaciones.

### Filtrando por tipo de relación

```cypher
MATCH (a)-[r:PARTICIPA_EN]->(p:Proyecto)
RETURN a, r, p
```

Ejecuta.

Ahora solo ves un tipo concreto.

### Variación: múltiples tipos en una consulta

```cypher
MATCH (a)-[r:AMIGO_DE|TRABAJA_CON]->(b)
RETURN a, b, r
```

Ejecuta.

Esto permite combinar tipos.

