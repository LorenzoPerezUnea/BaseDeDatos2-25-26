# Refactorización del grafo

Vamos a modificar estructura existente.

Ejemplo: añadir relación faltante entre proyecto y empresa.

```cypher
MATCH (e:Empresa)-[:GESTIONA]->(pr:Proyecto)
MERGE (pr)-[:PERTENECE_A]->(e)
```

Esto hace el modelo más consistente.

### Detectando nodos desconectados

```cypher
MATCH (p:Persona)
WHERE NOT (p)--()
RETURN p
```

Esto detecta entidades aisladas.

### Detectando relaciones débiles o poco útiles (sin propiedades)

```cypher
MATCH ()-[r]->()
WHERE size(keys(r)) = 0
RETURN r
```

Relaciones sin propiedades pueden ser sospechosas en ciertos contextos.

