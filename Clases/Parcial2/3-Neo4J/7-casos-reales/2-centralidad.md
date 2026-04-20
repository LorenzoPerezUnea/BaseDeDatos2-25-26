# Centralidad básica

Vamos a mirar cuántas relaciones tiene cada nodo.

```cypher
MATCH (p:Persona)-[r]-()
RETURN p.nombre, count(r) AS conexiones
ORDER BY conexiones DESC
```

Esto mide algo muy importante:

cuántas conexiones tiene cada persona.

Esto es una forma simple de centralidad.

# Interpretando centralidad

Una persona con muchas conexiones puede ser:

* alguien muy social
* alguien que conecta diferentes grupos
* alguien clave en la red

Pero cuidado:

no siempre más conexiones significa más importancia.


