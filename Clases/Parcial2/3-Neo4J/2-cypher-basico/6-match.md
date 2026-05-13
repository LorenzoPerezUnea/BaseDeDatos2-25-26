# Introduciendo MATCH como patrón

Hasta ahora has usado MATCH sin pensarlo demasiado.

Vamos a hacerlo consciente.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a, b
```

Esto no es “buscar”.

Esto es describir una forma dentro del grafo.

### Ejercicio guiado

Ahora modifica esta consulta:

* cambia el tipo de nodo
* añade una condición
* prueba varias combinaciones

Ejemplo:

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
WHERE b.edad > 30
RETURN a, r, b
```

Ejecuta, cambia, vuelve a ejecutar.

No busques la query perfecta.

Busca entender qué cambia cuando modificas el patrón.

Y quédate con esta idea:

cada consulta que escribes no es una instrucción, es una forma dentro del grafo.

