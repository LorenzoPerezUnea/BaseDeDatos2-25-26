# Introduciendo agregación básica

Ahora vamos a hacer algo nuevo: contar.

```cypher
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN e.nombre, count(p)
```

Ejecuta.

Esto devuelve el número total de nodos Persona.

Ahora algo más interesante:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
RETURN e.nombre, count(b)
```

Ejecuta.

Puede que el resultado no sea lo que esperabas.

Aquí falta algo.

