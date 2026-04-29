# Error típico: olvidar el alias de la relación

Vamos a provocar un error.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
WHERE intensidad > 6
RETURN a, b
```

Ejecuta.

Falla.

¿Por qué?

Porque intensidad pertenece a la relación, no al nodo.

Necesitas capturar la relación en una variable.

# Corrigiendo el error

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
WHERE r.intensidad > 6
RETURN a, r, b
```

Esto es algo que muchos alumnos olvidan.

