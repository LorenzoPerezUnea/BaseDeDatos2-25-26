# Cuando un path deja de ser solo un camino

Hasta ahora has usado paths para conectar nodos.

Ahora vamos a empezar a tratarlos como algo que contiene información en sí mismo.

No solo importa llegar de A a B.

Importa cómo llegas.

### Introduciendo nodos dentro del path

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
RETURN nodes(p)
```

Esto devuelve todos los nodos que forman el camino.

No solo el inicio y el final.

### Introduciendo relaciones dentro del path

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
RETURN relationships(p)
```

Ahora puedes ver cada conexión dentro del recorrido.

### Analizando el contenido del path

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
RETURN a.nombre, b.nombre, nodes(p), relationships(p)
```

Esto ya no es una consulta simple.

Es inspección estructural.


