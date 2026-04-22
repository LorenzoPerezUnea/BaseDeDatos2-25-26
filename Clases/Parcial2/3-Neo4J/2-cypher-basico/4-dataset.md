# Construyendo un dataset base

Ahora vamos a construir un pequeño mundo.

```cypher
CREATE (a:Persona {nombre: "Luis", edad: 30})
CREATE (b:Persona {nombre: "Carlos", edad: 28})
CREATE (c:Persona {nombre: "Marta", edad: 35})
CREATE (d:Persona {nombre: "Sofia", edad: 27})
```

Después:

```cypher
MATCH (n) RETURN n
```

No avances.

Observa.

Ahora ya no tienes un ejemplo, tienes un dataset.

### Ejercicio guiado

Vamos a añadir variación.

Añade tú una persona nueva.

No copies nombres.

Después ejecuta:

```cypher
MATCH (p:Persona) RETURN p
```

### Introduciendo relaciones con intención

Hasta ahora tienes nodos sueltos.

Eso no es interesante.

Un grafo empieza cuando conectas.

Antes de escribir, piensa:

¿Qué significa conectar dos personas?

Vamos a hacerlo:

```cypher
MATCH (a:Persona {nombre: "Marta"})
MATCH (b:Persona {nombre: "Luis"})
CREATE (a)-[:AMIGO_DE]->(b)
```

Ahora:

```cypher
MATCH (a)-[r]->(b)
RETURN a, r, b
```

Detente.

Mira la dirección.

No es una línea. Es una afirmación.

### Variación: duplicando relaciones

Ahora repite la misma relación:

```cypher
MATCH (a:Persona {nombre: "Marta"})
MATCH (b:Persona {nombre: "Luis"})
CREATE (a)-[:AMIGO_DE]->(b)
```

Consulta otra vez:

```cypher
MATCH (a)-[r]->(b)
RETURN a, r, b
```

Observa.

Hay duplicados.

Esto también es importante: las relaciones también pueden duplicarse.

