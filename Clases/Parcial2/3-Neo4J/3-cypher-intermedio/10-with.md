# Introduciendo WITH

Aquí aparece una palabra clave fundamental.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
WITH e, count(b) AS conexiones
WHERE conexiones > 1
RETURN e.nombre, conexiones
```

Ejecuta.

WITH actúa como un paso intermedio.

Esto es clave: te permite transformar datos y seguir trabajando con ellos.

### Variación para entender WITH

Vamos a modificar ligeramente:

```cypher
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa)
WITH e.nombre AS empresa, count(p) AS total
RETURN empresa, total
```

Ejecuta.

Ahora ya no tienes el nodo completo, solo el nombre.

Esto es importante: WITH define qué variables sobreviven.

### Error típico con WITH

Vamos a provocar un error.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
WITH count(b) AS amigos
RETURN a.nombre, amigos
```

Ejecuta.

Falla.

¿Por qué?

Porque a no pasó por el WITH.

Este error es muy común.

