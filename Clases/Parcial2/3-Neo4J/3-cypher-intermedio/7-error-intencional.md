# Error intencional con agregación

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a.nombre, b.nombre, count(b)
```

Ejecuta.

Puede dar resultados confusos.

Esto pasa porque estás mezclando variables no agregadas con agregadas.

Este tipo de errores es muy común.

### Corrigiendo el error

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a.nombre, count(b)
```

Mantén coherencia en lo que devuelves.



