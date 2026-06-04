# Cuando la relación cambia el resultado

Vamos a ver cómo eso afecta directamente a los recorridos y a las consultas más complejas.

Antes de avanzar, vuelve a mirar tu grafo.

```cypher
MATCH (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre, e.nombre
```

No avances.

Observa que ahora tienes:

* distintos tipos de relaciones
* relaciones con propiedades
* incluso varias relaciones entre los mismos nodos

Esto cambia completamente cómo debes escribir consultas.

### Pensando en recorridos con condiciones

Hasta ahora has recorrido grafos sin preocuparte por qué tipo de relación estabas siguiendo.

Ahora vamos a hacerlo con intención.

```cypher
MATCH (a:Persona)-[r:AMIGO_DE*1..3]->(b:Persona)
RETURN a, r, b
```

Ejecuta.

Esto recorre cualquier relación AMIGO\_DE sin importar sus propiedades.

Ahora vamos a introducir una idea importante: no todos los caminos son iguales.

