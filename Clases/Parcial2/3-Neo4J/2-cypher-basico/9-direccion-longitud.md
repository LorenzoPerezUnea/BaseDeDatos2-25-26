# Direccionalidad y Longitud

### Direccionalidad y su impacto

Vamos a observar algo que parece pequeño pero cambia todo.

```cypher
MATCH (a)-[r:AMIGO_DE]->(b)
RETURN a, r, b
```

Ahora prueba:

```cypher
MATCH (a)-[r:AMIGO_DE]-(b)
RETURN a, r, b
```

Sin flecha.

Ejecuta ambas y compara.

En el segundo caso, estás ignorando la dirección.

Esto es útil, pero también puede introducir resultados que no esperabas.

### Introduciendo longitudes variables

Ahora vamos a trabajar con recorridos más complejos.

```cypher
MATCH (a)-[r:AMIGO_DE*2]->(b)
RETURN a, r, b
```

Esto busca caminos de longitud 2.

Ahora:

```cypher
MATCH (a)-[r:AMIGO_DE*1..3]->(b)
RETURN a, r, b
```

Esto busca entre 1 y 3 saltos.

Antes de ejecutar, piensa: ¿qué debería devolver?

Ejecuta y compara.

### Variación sin límites

```cypher
MATCH (a)-[r:AMIGO_DE*]->(b)
RETURN a, r, b
```

Ejecuta.

Observa.

Puede devolver muchos resultados.

Aquí aparece una idea clave: los grafos crecen rápido en profundidad.

### Controlando resultados

Para evitar perder control:

```cypher
MATCH (a)-[r:AMIGO_DE*1..3]->(b)
RETURN a, r, b
LIMIT 10
```

Ejecuta.

Esto no cambia el patrón, pero sí hace manejable el resultado.

