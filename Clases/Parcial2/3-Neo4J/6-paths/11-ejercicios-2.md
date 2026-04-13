# Ejercicios

### Ejercicio guiado

Encontrar caminos que conectan proyectos distintos

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (a)-[:PARTICIPA_EN]->(p1:Proyecto)
MATCH (b)-[:PARTICIPA_EN]->(p2:Proyecto)
WHERE p1 <> p2
RETURN a.nombre, p1.nombre, p2.nombre
```

### Ejercicio guiado 2

Encontrar caminos “fuertes” entre ciudades

```cypher
MATCH p = (a:Persona)-[r:AMIGO_DE*1..3]->(b:Persona)
MATCH (a)-[:VIVE_EN]->(c1:Ciudad)
MATCH (b)-[:VIVE_EN]->(c2:Ciudad)
WHERE ALL(rel IN r WHERE rel.intensidad > 6) AND c1 <> c2
RETURN c1.nombre, c2.nombre, count(p)
ORDER BY count(p) DESC
```

### Ejercicio guiado 3

encontrar personas conectadas a proyectos a través de relaciones sociales

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:PARTICIPA_EN]->(pr:Proyecto)
RETURN a.nombre, pr.nombre
```

Modifica:

* limita la distancia
* añade DISTINCT
* ordena por longitud del path

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..2]->(b:Persona)
MATCH (b)-[:PARTICIPA_EN]->(pr:Proyecto)
RETURN DISTINCT 
  a.nombre AS persona,
  pr.nombre AS proyecto,
  length(p) AS distancia
ORDER BY distancia ASC
```

o mejor:

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..2]->(b:Persona)
MATCH (b)-[:PARTICIPA_EN]->(pr:Proyecto)
RETURN DISTINCT 
  a.nombre AS persona,
  pr.nombre AS proyecto,
  length(p) AS distancia,
  nodes(p) AS camino
ORDER BY distancia ASC, persona
```

