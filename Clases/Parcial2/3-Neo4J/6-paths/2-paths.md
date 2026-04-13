# Introduciendo paths

```cypher
MATCH (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre, e.nombre
```

Aquí aparece algo nuevo:

[:AMIGO\_DE\*1..3]

Esto significa:

recorre entre 1 y 3 relaciones consecutivas

### Observando el comportamiento real

Ejecuta la consulta varias veces.

Mira los resultados.

Vas a notar algo:

* aparecen combinaciones repetidas
* el número de resultados crece rápido
* no todos los caminos son igual de relevantes

Esto es importante.

Los paths generan volumen.

### Limitando resultados con DISTINCT

```cypher
MATCH (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
RETURN DISTINCT a.nombre, e.nombre
```

Esto limpia el resultado.

Pero no controla el recorrido.


