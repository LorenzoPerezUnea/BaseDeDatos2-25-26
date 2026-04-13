# Probando lo que antes no se podía

```cypher
MATCH (p1:Persona)-[:PARTICIPA_EN]->(pr:Proyecto)<-[:PARTICIPA_EN]-(p2:Persona)
WHERE p1.nombre <> p2.nombre
RETURN p1.nombre, p2.nombre, pr.nombre
```

Esto ahora sí es posible.

### Detectando redundancia en el modelo

Vamos a observar otra situación.

En el dataset ya tienes:

* Persona → TRABAJA\_EN → Empresa
* Empresa → GESTIONA → Proyecto

Pero también:

* Persona → PARTICIPA\_EN → Proyecto

Esto puede generar redundancia.

### Analizando dos caminos equivalentes

```cypher
MATCH (p:Persona)-[r:PARTICIPA_EN]->(pr:Proyecto)
RETURN p, pr, r
```

```cypher
MATCH (p:Persona)-[t:TRABAJA_EN]->(e:Empresa)-[g:GESTIONA]->(pr:Proyecto)
RETURN p, pr, t, g, e
```

Dos formas de llegar al mismo sitio.

Pero no son equivalentes semánticamente.

### Decidiendo qué mantener

Pregunta clave:

¿participar en un proyecto implica trabajar en la empresa?

Si la respuesta es sí, puedes simplificar.

Si no, necesitas ambos caminos.

El modelo depende del dominio, no de la herramienta.

