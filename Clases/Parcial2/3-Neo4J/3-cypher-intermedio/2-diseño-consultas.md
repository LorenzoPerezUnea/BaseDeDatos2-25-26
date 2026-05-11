# Pensar primero, escribir después

Vamos a plantear un objetivo simple:

quiero obtener los nombres de las personas y los nombres de sus amigos.

Antes de escribir, piensa cómo se representa eso en el grafo.

Tienes nodos Persona conectados por relaciones AMIGO\_DE.

Ahora sí, escribe:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre, b.nombre, e.nombre
```

Ejecuta.

Este tipo de consulta ya no devuelve nodos completos, devuelve propiedades concretas.

Esto es importante: empiezas a controlar qué información extraes.

### Variación: cambiando lo que devuelves

Vamos a modificar solo el RETURN.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (a)-[:VIVE_EN]->(c:Ciudad)
RETURN a, b, c
```

Ejecuta.

Ahora vuelve a:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:PARTICIPA_EN]->(p:Proyecto)
RETURN a.nombre, p.nombre
```

Observa.

El patrón no cambia. Solo cambia la proyección.

Este concepto es clave: MATCH define, RETURN selecciona.

