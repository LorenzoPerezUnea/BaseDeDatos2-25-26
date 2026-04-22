# Pensando en el grafo como red

Vamos a hacer una pausa conceptual.

Ejecuta:

```cypher
MATCH (n) RETURN n
```

Después:

```cypher
MATCH (a)-[r]->(b) RETURN a, r, b
```

No mires solo datos.

Mira conexiones.

Un error común es seguir pensando en tablas. Aquí necesitas pensar en redes.

### Variación guiada sobre paths

Vamos a modificar ligeramente:

```cypher
MATCH (a:Persona {nombre: "Luis"})-[r:AMIGO_DE*1..3]->(b)
RETURN a, r, b
```

Ejecuta.

Ahora cambia:

* el nombre inicial
* la profundidad (1..2, 1..4)

Ejecuta varias veces.

Observa cómo cambia el alcance del grafo.

