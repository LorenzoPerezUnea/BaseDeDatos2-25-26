# Ejercicios

### Ejercicio guiado

Objetivo:

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

### Ejercicio guiado 2

Encontrar personas conectadas con ciudades distintas a la suya

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..2]->(b:Persona)
MATCH (a)-[:VIVE_EN]->(c1:Ciudad)
MATCH (b)-[:VIVE_EN]->(c2:Ciudad)
WHERE c1 <> c2
RETURN a.nombre, c1.nombre, c2.nombre
```

Aquí ya estás cruzando información a través de paths.


