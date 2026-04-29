# Ejercicio guiado

Construye una consulta que:

* use propiedades de relaciones
* combine al menos dos niveles
* filtre resultados
* ordene

Base:

```cypher
MATCH (a:Persona)-[r1:AMIGO_DE]->(b:Persona)-[r2:AMIGO_DE]->(c:Persona)
MATCH (c)-[:VIVE_EN]->(ci:Ciudad)
WHERE r1.intensidad > 5
RETURN a.nombre, ci.nombre
```

Modifica:

* añade condiciones
* añade ORDER BY
* cambia el recorrido

Ejecuta varias veces.

