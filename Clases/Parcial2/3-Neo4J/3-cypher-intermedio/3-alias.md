# Introduciendo alias en resultados

Vamos a mejorar la legibilidad.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre AS origen, e.nombre AS empresa
```

Ejecuta.

Esto no cambia los datos, pero sí cómo los interpretas.

En consultas más grandes esto es fundamental.

### Error típico: olvidar qué variable es qué

Vamos a provocar un error conceptual.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN nombre
```

Ejecuta.

Esto falla.

¿Por qué?

Porque nombre no es una variable, es una propiedad.

Esto es algo que muchos alumnos confunden al principio.

