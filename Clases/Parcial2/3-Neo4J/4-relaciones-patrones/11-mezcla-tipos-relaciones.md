# Introduciendo mezcla de tipos de relaciones

Ahora vamos a combinar tipos.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)-[:TRABAJA_EN]->(e:Empresa)-[:GESTIONA]->(p:Proyecto)
RETURN a.nombre, p.nombre
```

Ejecuta.

Esto mezcla contextos: amistad y trabajo.

### Variación con filtros

```cypher
MATCH (a:Persona)-[r1:AMIGO_DE]->(b:Persona)-[r2:TRABAJA_EN]->(e:Empresa)
WHERE r1.intensidad > 5 AND e.sector = "Tecnologia"
RETURN a, e, r1, r2
```

Observa.

Puedes filtrar solo parte del recorrido.

### Error típico: asumir simetría

Vamos a provocar un error conceptual.

```cypher
MATCH (a:Persona)-[t:TRABAJA_CON]-(b:Persona)
MATCH (b)-[v:VIVE_EN]->(c:Ciudad)
RETURN b, a, c, t, v
```

Esto no invierte la relación.

Solo cambia el orden en el RETURN.

La dirección sigue siendo la misma.

### Corrigiendo el modelo mental

Si quieres ignorar dirección:

```cypher
MATCH (b:Persona)-[t:TRABAJA_CON]-(a:Persona)
MATCH (a)-[v:VIVE_EN]->(c:Ciudad)
RETURN a, b, c, t, v
```

Esto sí cambia el comportamiento.

### Diferencia en los resultados cambiando el sentido de la relación

| Patrón  | Significado         |
| ---------- | --------------------- |
| `->` | dirección estricta |
| `<-` | dirección inversa  |
| `-`  | ignora dirección   |

ejemplos:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a.nombre, b.nombre
```

```cypher
MATCH (a:Persona)<-[:AMIGO_DE]-(b:Persona)
RETURN a.nombre, b.nombre
```

o más precisamente:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
WHERE a.nombre = "Luis"
RETURN b.nombre
```

```cypher
MATCH (a:Persona)<-[:AMIGO_DE]-(b:Persona)
WHERE a.nombre = "Luis"
RETURN b.nombre
```

