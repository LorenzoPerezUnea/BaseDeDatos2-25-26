# Añadiendo propiedades a relaciones

Vamos a modificar el grafo.

```cypher
MATCH (a:Persona {nombre: "Ana"})
MATCH (b:Persona {nombre: "Luis"})
CREATE (a)-[:TRABAJA_CON {proyecto: "Gaia", horas: 120}]->(b)
```

Ejecuta.

Ahora consulta:

```cypher
MATCH (a:Persona)-[r]->(b)
RETURN a, r, b
```

Observa.

La relación ahora tiene propiedades.

Esto cambia completamente cómo puedes consultar.

### Variación: múltiples relaciones con distinto significado

Vamos a añadir otra relación entre los mismos nodos.

```cypher
MATCH (a:Persona {nombre: "Ana"})
MATCH (b:Persona {nombre: "Luis"})
CREATE (a)-[:TRABAJA_CON {proyecto: "Apollo", horas: 60}]->(b)
```

Consulta otra vez:

```cypher
MATCH (a:Persona)-[r]->(b)
RETURN a, r, b
```

Ahora hay varias relaciones entre los mismos nodos.

Esto es algo que en SQL sería complicado de modelar.

### Pensando en el significado de múltiples relaciones

Haz una pausa.

¿Qué significa tener dos relaciones entre los mismos nodos?

Puede representar:

* distintas etapas en el tiempo
* distintos contextos
* distintos tipos de interacción

Esto no es un problema, es una capacidad.

