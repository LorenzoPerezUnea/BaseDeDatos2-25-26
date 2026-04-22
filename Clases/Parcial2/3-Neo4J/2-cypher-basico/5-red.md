# Construyendo una pequeña red

Vamos a ampliar esto.

```cypher
MATCH (l:Persona {nombre: "Luis"})
MATCH (c:Persona {nombre: "Carlos"})
MATCH (m:Persona {nombre: "Marta"})
CREATE (l)-[:AMIGO_DE]->(c)
CREATE (c)-[:AMIGO_DE]->(m)
```

Después:

```cypher
MATCH (a)-[r]->(b)
RETURN a, r, b
```

Ahora empieza a aparecer algo interesante: estructura.

### Pensando antes de consultar

Vamos a hacer algo diferente.

Antes de escribir la siguiente query, piensa:

Si Luis es amigo de Carlos y Carlos de Marta,
¿cómo encontrarías a Marta desde Luis?

Ahora ejecuta:

```cypher
MATCH (a)-[:AMIGO_DE]->()-[:AMIGO_DE]->(c)
RETURN a, c
```

o más precisamente:

```cypher
MATCH (a:Persona {nombre: "Luis"})-[r1:AMIGO_DE]->(b)-[r2:AMIGO_DE]->(c:Persona)
RETURN a, b, c, r1, r2
```

Observa.

Esto es un recorrido.

### Variación del recorrido

Vamos a hacerlo más profundo.

```cypher
MATCH (a)-[:AMIGO_DE]->()-[:AMIGO_DE]->()-[:AMIGO_DE]->(d)
RETURN a, d
```

o mas precisamente

```cypher
MATCH (a)-[r1:AMIGO_DE]->(b)-[r2:AMIGO_DE]->(c)-[r3:AMIGO_DE]->(d)
RETURN a, r1, b, r2, c, r3, d
```

Ejecuta.

Aunque no siempre haya resultados, esto te enseña algo importante: puedes describir caminos.

### comparación real con SQL

Piensa en esto:

Para hacer esto en SQL necesitarías:

* varias tablas
* varios joins
* lógica más compleja

Aquí es una sola expresión.

No es solo más corto. Es más cercano a cómo piensas.

