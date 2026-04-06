# Introduciendo DISTINCT

Ahora vamos a evitar duplicados.

```cypher
MATCH (p:Persona)-[:VIVE_EN]->(c:Ciudad)
RETURN DISTINCT c.nombre
```

Ejecuta.

Ahora cada nombre aparece una sola vez.

# Variación con DISTINCT y conteo

```cypher
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN count(DISTINCT e)
```

Ejecuta.

Esto cuenta nodos únicos.

# Ejercicio guiado

Ahora intenta responder:

¿cuántas personas tienen al menos un amigo y en que ciudad vive este amigo?

Pista:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:VIVE_EN]->(c:Ciudad)
RETURN count(DISTINCT c)a)
```

Ejecuta y piensa si responde exactamente a la pregunta.

