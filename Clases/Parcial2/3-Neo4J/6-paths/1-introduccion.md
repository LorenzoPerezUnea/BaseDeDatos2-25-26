# Consultas complejas y paths

### Cuando las consultas dejan de ser lineales

Hasta ahora has escrito consultas que, aunque combinaban varias partes, seguían siendo relativamente directas.

En esta clase vamos a entrar en otro nivel.

Ya no vas a escribir una sola consulta.

Vas a construir una solución paso a paso.

### El problema de las consultas grandes

Empieza con algo que parece simple.

Personas que tienen amigos que trabajan en empresas.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre, e.nombre
```

Funciona.

Pero ahora cambia el problema:

personas que están conectadas indirectamente con empresas a través de relaciones sociales

Eso ya no es un salto.

Es un recorrido.


