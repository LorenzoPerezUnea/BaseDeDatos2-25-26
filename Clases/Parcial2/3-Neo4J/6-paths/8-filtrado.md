# Introduciendo filtrado por nodos intermedios

Queremos paths donde aparezca una persona concreta en medio.

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
WHERE any(n IN nodes(p) WHERE n.nombre = "Luis")
RETURN a.nombre, b.nombre
```

Esto introduce algo nuevo:

analizar el contenido del path.

### Variación: evitando nodos concretos

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
WHERE NONE(n IN nodes(p) WHERE n.nombre = "Carlos")
RETURN a.nombre, b.nombre
```

Esto cambia completamente el resultado.

### Introduciendo condiciones sobre relaciones del path

```cypher
MATCH p = (a:Persona)-[r:AMIGO_DE*1..3]->(b:Persona)
WHERE ALL(rel IN r WHERE rel.intensidad > 6)
RETURN a.nombre, b.nombre
```

Ahora no solo importa la estructura.

Importan las propiedades de cada paso.


