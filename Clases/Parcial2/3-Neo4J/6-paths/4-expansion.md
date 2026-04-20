# Problema típico: explosión combinatoria

Si aumentas esto:

```cypher
[:AMIGO_DE*1..5]
```

El número de resultados puede crecer mucho.

Esto no es un error.

Es una propiedad de los grafos.

### Introduciendo filtros sobre nodos intermedios

Vamos a hacer algo más interesante.

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:VIVE_EN]->(c:Ciudad)
WHERE c.nombre = "Madrid"
RETURN a.nombre, b.nombre, length(p) as long
```

Aquí ya estás combinando path + condición.

### Introduciendo combinación con trabajo

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
WHERE e.sector = "Tecnologia"
RETURN a.nombre, e.nombre, length(p) as long
```

Esto empieza a parecer una consulta real.

### Controlando el punto final del path

Otra forma de escribirlo:

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre, e.nombre,  length(p) as long
```

Esto integra todo en un solo patrón.

