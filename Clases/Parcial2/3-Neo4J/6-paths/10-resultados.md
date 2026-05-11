# Interpretando resultados

Más caminos puede significar:

* mayor conexión
* mayor redundancia
* mayor influencia

No es automático, pero es una señal.

### Introduciendo combinación con ciudades

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:VIVE_EN]->(c:Ciudad)
RETURN c.nombre, count(DISTINCT b) AS personas
ORDER BY personas DESC
```

o también:

```cypher
MATCH (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:VIVE_EN]->(c:Ciudad)
RETURN c.nombre, collect(DISTINCT b.nombre) AS personas, count(DISTINCT b) AS total
ORDER BY total DESC
```

Esto empieza a parecer análisis.

### Introduciendo nodos puente

Queremos encontrar personas que aparecen mucho en caminos.

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
UNWIND nodes(p) AS n
RETURN n.nombre, count(*) AS apariciones
ORDER BY apariciones DESC
```

Esto identifica nodos clave.

### Introduciendo paths entre contextos distintos

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (a)-[:TRABAJA_EN]->(e1:Empresa)
MATCH (b)-[:TRABAJA_EN]->(e2:Empresa)
WHERE e1 <> e2
RETURN a.nombre, e1.nombre, e2.nombre
```

Esto detecta conexiones entre empresas.


