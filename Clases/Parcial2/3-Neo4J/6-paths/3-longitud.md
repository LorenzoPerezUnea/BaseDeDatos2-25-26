# Introduciendo variable de path

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
RETURN p
```

Ahora no solo obtienes nodos.

Obtienes el camino completo.

### Analizando la longitud del path

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
RETURN a.nombre, b.nombre, length(p) as long
ORDER BY long DESC
```

Esto añade información clave:

cuántos pasos hay entre nodos

### Control del recorrido

No todos los paths tienen sentido.

Vamos a limitar.

```cypher
MATCH p = (a:Persona)-[r:AMIGO_DE*1..2]->(b:Persona)
WHERE a <> b
RETURN a, b, r, length(p)
```

Reducir profundidad cambia completamente el resultado.

