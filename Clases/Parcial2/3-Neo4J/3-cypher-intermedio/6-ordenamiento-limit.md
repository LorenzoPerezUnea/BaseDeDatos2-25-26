# Introduciendo ordenación

Vamos a ordenar resultados.

```cypher
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN e.nombre, count(p) AS empleados
ORDER BY empleados DESC
```

Ejecuta.

Ahora puedes ver quién tiene más conexiones.

### Pensando en consultas útiles

Preguntas que ahora puedes responder:

* ¿quién tiene más amigos?
* ¿quién está más conectado?

Esto es muy difícil de ver en SQL sin joins complejos.

### Introduciendo LIMIT en análisis

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a.nombre, count(b) AS amigos
ORDER BY amigos DESC
LIMIT 3
```

Ejecuta.

Esto te da el top 3.

Aquí ya estás haciendo algo cercano a análisis real.

