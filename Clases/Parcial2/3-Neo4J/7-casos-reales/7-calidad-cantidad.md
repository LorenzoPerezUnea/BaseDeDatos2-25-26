# Filtrado de calidad en paths

```cypher
MATCH p = (a:Persona)-[r:AMIGO_DE*1..3]->(b:Persona)
WHERE ALL(rel IN r WHERE rel.intensidad > 6)
RETURN a.nombre, b.nombre, length(p)
```

Aquí solo consideras caminos fuertes.

# Interpretando calidad vs cantidad

No todos los caminos valen lo mismo.

* muchos caminos débiles
* pocos caminos fuertes

Ambos dicen cosas distintas.

