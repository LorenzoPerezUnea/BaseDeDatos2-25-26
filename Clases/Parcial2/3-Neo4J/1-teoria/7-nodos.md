# Redes de nodos

### Crear múltiples nodos

Vamos a ampliar un poco el escenario.

```cypher
CREATE (a:Persona {nombre: "Luis", edad: 30})
CREATE (b:Persona {nombre: "Carlos", edad: 28})
CREATE (c:Persona {nombre: "Marta", edad: 35})
```

Ejecuta estas instrucciones y luego vuelve a lanzar:

```cypher
MATCH (n) RETURN n
```

Ahora deberías ver varios nodos en pantalla.

Tómate un momento para observar cómo Neo4j los organiza automáticamente.

### Crear relaciones entre nodos

Hasta ahora tenemos nodos aislados. Vamos a conectarlos.

```cypher
MATCH (a:Persona {nombre: "Carlos"})
MATCH (b:Persona {nombre: "Luis"})
CREATE (a)-[:AMIGO_DE]->(b)
```

Ejecuta esto y luego consulta:

```cypher
MATCH (a)-[r]->(b)
RETURN a, r, b
```

Acabas de crear tu primera relación.

Observa que ahora no solo hay nodos, sino también una conexión entre ellos.

### Construyendo una pequeña red

Vamos a ampliar la red con más conexiones.

```cypher
MATCH (l:Persona {nombre: "Luis"})
MATCH (c:Persona {nombre: "Carlos"})
MATCH (m:Persona {nombre: "Marta"})
CREATE (l)-[:AMIGO_DE]->(c)
CREATE (c)-[:AMIGO_DE]->(m)
```

Después ejecuta:

```cypher
MATCH (a)-[r]->(b)
RETURN a, r, b
```

Ahora tienes un pequeño grafo con varias personas conectadas.

Este tipo de estructura es la base de muchos sistemas reales.

