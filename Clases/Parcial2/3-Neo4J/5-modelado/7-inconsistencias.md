# Detectando inconsistencias

Vamos a buscar incoherencias.

```cypher
MATCH (p:Persona)-[:PARTICIPA_EN]->(pr:Proyecto)
MATCH (pr)-[:PERTENECE_A]->(e:Empresa)
WHERE NOT (p)-[:TRABAJA_EN]->(e)
RETURN p, pr, e
```

Esto detecta personas que participan en proyectos de empresas donde no trabajan.

Esto es análisis de calidad del modelo.

### Introduciendo relaciones derivadas

A veces puedes crear relaciones nuevas basadas en otras.

```cypher
MATCH (p:Persona)-[:PARTICIPA_EN]->(pr:Proyecto)-[:PERTENECE_A]->(e:Empresa)
MERGE (p)-[:COLABORA_CON_EMPRESA]->(e)
```

Esto simplifica consultas futuras.

Pero añade duplicación.

### Evaluando el coste de simplificar

Consulta original:

```cypher
MATCH (p:Persona)-[:PARTICIPA_EN]->(pr:Proyecto)-[:PERTENECE_A]->(e:Empresa)
RETURN p, e
```

Consulta simplificada:

```cypher
MATCH (p:Persona)-[:COLABORA_CON_EMPRESA]->(e:Empresa)
RETURN p, e
```

Más simple, pero menos explícita.


