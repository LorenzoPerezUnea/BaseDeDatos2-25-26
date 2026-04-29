# Filtrando por propiedades de relaciones

Ahora vamos a usar esas propiedades.

```cypher
MATCH (a)-[r:TRABAJA_CON]->(b)
WHERE r.horas > 80
RETURN a, b, r
```

Ejecuta.

Ahora estás filtrando no por nodos, sino por relaciones.

Esto es un cambio importante.

### Variación: filtro combinado

```cypher
MATCH (a:Persona)-[r:TRABAJA_CON]->(b:Persona)
MATCH (a)-[:TRABAJA_EN]->(e:Empresa)
MATCH (b)-[:TRABAJA_EN]->(e)
WHERE r.horas > 80 AND e.sector = "Tecnologia"
RETURN a. b, e, r
```

o mejor :

```cypher
MATCH (a:Persona)-[r:TRABAJA_CON]->(b:Persona)
MATCH (a)-[:TRABAJA_EN]->(e:Empresa)
MATCH (b)-[:TRABAJA_EN]->(e)
WHERE r.horas > 80 AND e.sector = "Tecnologia"
RETURN DISTINCT a.nombre, b.nombre, e.nombre, r.horas
```

Ejecuta.

Ahora combinas información de nodos y relaciones.

