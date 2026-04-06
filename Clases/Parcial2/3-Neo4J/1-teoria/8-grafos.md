# Grafos

### Recorrido de un grafo

Aquí empieza lo interesante.

Vamos a consultar relaciones específicas:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a, b
```

Esto devuelve todas las relaciones de amistad.

Pero ahora vamos un paso más allá.

### Amigos de amigos

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->()-[:AMIGO_DE]->(c:Persona)
RETURN a, c
```

Fíjate en algo clave: no necesitamos joins ni lógica compleja.

Estamos describiendo un patrón de recorrido.

Este tipo de consulta es precisamente lo que hace que los grafos sean tan potentes.

### Ejercicio guiado

Ahora te toca modificar el grafo.

Objetivo:

* añade una nueva persona
* conéctala con al menos dos nodos existentes
* consulta el grafo completo

Puedes usar como referencia:

```cypher
CREATE (n:Persona {nombre: "Sofia", edad: 27})
```

resolución:

```cypher
MATCH (s:Persona {nombre: "Sofia"})
MATCH (c:Persona {nombre: "Carlos"})
MATCH (l:Persona {nombre: "Luis"})
CREATE (s)-[:AMIGO_DE]->(c)
CREATE (s)-[:AMIGO_DE]->(l)
```

Después conecta y consulta.

Este paso es importante porque empieza a construir intuición.

