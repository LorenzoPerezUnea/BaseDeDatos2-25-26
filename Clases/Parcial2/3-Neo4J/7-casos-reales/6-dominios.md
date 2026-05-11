# Análisis entre dominios

Ahora mezclamos información.

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (a)-[:TRABAJA_EN]->(e1:Empresa)
MATCH (b)-[:TRABAJA_EN]->(e2:Empresa)
WHERE e1 <> e2
RETURN e1.nombre, e2.nombre, count(p)
ORDER BY count(p) DESC
```

Esto conecta empresas a través de relaciones sociales.

# Interpretando conexiones entre empresas

Esto puede indicar:

* colaboración indirecta
* movilidad de talento
* relaciones ocultas entre organizaciones

El grafo empieza a revelar estructura.

# Concentración geográfica

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:VIVE_EN]->(c:Ciudad)
RETURN c.nombre, count(p)
ORDER BY count(p) DESC
```

Esto muestra ciudades con más actividad en paths.

# Interpretando concentración

Puede indicar:

* hubs sociales
* concentración de conexiones
* puntos clave del grafo

