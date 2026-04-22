# Introduciendo consultas más cercanas a negocio

Vamos a construir una consulta más real.

Objetivo:

personas que tienen relaciones fuertes y además están conectadas indirectamente.

```cypher
MATCH (a:Persona)-[r1:AMIGO_DE]->(b:Persona)-[:TRABAJA_EN]->(e:Empresa)
MATCH (b)-[r2:AMIGO_DE]->(c:Persona)
WHERE r1.intensidad > 6 AND r2.intensidad > 6
RETURN a.nombre, e.nombre, c.nombre
```

Ejecuta.

Esto ya es lógica de negocio.

### Variación con ordenación

```cypher
MATCH (a:Persona)-[r1:AMIGO_DE]->(b:Persona)-[r2:AMIGO_DE]->(c:Persona)
MATCH (c)-[:TRABAJA_EN]->(e)
WHERE r1.intensidad > 6 AND r2.intensidad > 6
RETURN a.nombre, e.nombre, r2.intensidad
ORDER BY r2.intensidad DESC
```

Ejecuta.

Ahora no solo consultas, analizas.

### Introduciendo combinación con WITH

Vamos a dividir el problema.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
WITH e, count(b) AS conexiones
WHERE conexiones > 1
RETURN e.nombre, conexiones
```

Ejecuta.

Esto mezcla lo visto en la clase anterior con relaciones enriquecidas.

