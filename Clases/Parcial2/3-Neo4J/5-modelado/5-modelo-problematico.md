# Partiendo de un modelo problemático

Imagina que recibes un sistema ya construido. No lo has diseñado tú. Solo sabes que “funciona”, pero las consultas son difíciles y los resultados no siempre son claros.

Vamos a simular esa situación.

```cypher
CREATE (p:Persona {
  nombre: "Paula",
  empresa: "OmegaTech",
  ciudad: "Sevilla",
  proyecto: "Hades"
})
```

A simple vista parece práctico.

Pero en cuanto intentas hacer consultas reales, aparecen los problemas.

```cypher
MATCH (p:Persona {empresa: "OmegaTech"})
RETURN p
```

Funciona.

Pero ahora intenta responder:

personas que trabajan en el mismo proyecto que alguien

No hay forma de recorrer nada.

### Primer paso: separar entidades

Vamos a empezar a transformar el modelo.

```cypher
CREATE (p:Persona {nombre: "Paula"})
CREATE (e:Empresa {nombre: "OmegaTech"})
CREATE (c:Ciudad {nombre: "Sevilla"})
CREATE (pr:Proyecto {nombre: "Hades"})
```

Ahora ya tienes entidades reales.

### Segundo paso: crear relaciones explícitas

```cypher
MATCH (p:Persona {nombre: "Paula"})
MATCH (e:Empresa {nombre: "OmegaTech"})
MATCH (c:Ciudad {nombre: "Sevilla"})
MATCH (pr:Proyecto {nombre: "Hades"})

CREATE (p)-[:TRABAJA_EN]->(e)
CREATE (p)-[:VIVE_EN]->(c)
CREATE (p)-[:PARTICIPA_EN]->(pr)
```

Ahora el grafo es navegable.

