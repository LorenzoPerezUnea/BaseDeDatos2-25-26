# Ejercicios

### Ejercicio guiado

Objetivo:

detectar personas que:

* trabajan en una empresa
* viven en una ciudad
* pero no tienen ninguna relación social

```cypher
MATCH (p:Persona)-[t:TRABAJA_EN]->(e:Empresa)
MATCH (p)-[v:VIVE_EN]->(c:Ciudad)
WHERE NOT (p)-[:AMIGO_DE]->()
RETURN p, e, c, t, v
```

### Ejercicio de refactorización

Crear una relación directa entre personas que trabajan en la misma empresa

```cypher
MATCH (p1:Persona)-[:TRABAJA_EN]->(e:Empresa)<-[:TRABAJA_EN]-(p2:Persona)
WHERE p1 <> p2
MERGE (p1)-[:ES_COLEGA_DE]->(p2)
```

Esto cambia completamente cómo puedes consultar el grafo después.

