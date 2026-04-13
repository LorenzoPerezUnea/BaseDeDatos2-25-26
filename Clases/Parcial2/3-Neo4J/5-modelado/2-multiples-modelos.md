# Un mismo problema, múltiples modelos

Imagina este escenario:

Personas trabajan en empresas y participan en proyectos.

Pregunta:

¿cómo modelarías esto?

Antes de escribir nada, piensa.

Hay varias formas de hacerlo.

Vamos a ver dos.

### Modelo 1: directo y simple

```cypher
CREATE (p:Persona {nombre: "Juana"})
CREATE (e:Empresa {nombre: "SocialCorp"})
CREATE (pr:Proyecto {nombre: "Demeter"})

CREATE (p)-[:TRABAJA_EN]->(e)
CREATE (p)-[:PARTICIPA_EN]->(pr)
```

Este modelo es claro.

Pero ahora piensa:

¿qué pasa si queremos saber en qué proyecto trabaja dentro de la empresa?

No hay conexión directa.

El modelo empieza a quedarse corto.

### Modelo 2: introduciendo contexto en relaciones

```cypher
MATCH (p:Persona {nombre: "Juana"})
MATCH (e:Empresa {nombre: "SocialCorp"})
MATCH (pr:Proyecto {nombre: "Demeter"})

CREATE (p)-[:TRABAJA_EN {proyecto: "Hermes"}]->(e)
```

Aquí introduces el proyecto como propiedad.

Ahora puedes responder más cosas.

Pero surge otra pregunta:

¿qué pasa si una persona trabaja en varios proyectos en la misma empresa?

El modelo empieza a forzarse.

### Modelo 3: proyecto como nodo intermedio

```cypher
MATCH (p:Persona {nombre: "Juana"})
MATCH (e:Empresa {nombre: "SocialCorp"})
MATCH (pr:Proyecto {nombre: "Demeter"})

CREATE (p)-[:PARTICIPA_EN]->(pr)
CREATE (pr)-[:PERTENECE_A]->(e)
```

Este modelo es más flexible.

Ahora puedes:

* conectar múltiples personas al mismo proyecto
* conectar proyectos con empresas
* añadir información al proyecto

Pero también introduce más complejidad.

### Primera lección importante

No existe un único modelo correcto.

Existe un modelo adecuado para lo que quieres consultar.

Esto es clave:

modelas para consultar, no para almacenar

