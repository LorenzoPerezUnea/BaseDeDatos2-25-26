# Error típico: separar patrones sin relación

Vamos a provocar un error muy común.

```cypher
MATCH (a:Persona)
WHERE a.edad > 30
MATCH (b:Persona)
RETURN a, b
```

Ejecuta.

Verás combinaciones que no tienen sentido.

Esto pasa porque no hay ninguna relación entre a y b.

Este error es equivalente a hacer un producto cartesiano en SQL sin querer.

### Corrigiendo el patrón

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
WHERE a.edad > 30
RETURN a, r, b
```

Ahora sí hay estructura.

Aquí aparece una regla importante: en grafos, la relación es lo que da sentido a los datos.

