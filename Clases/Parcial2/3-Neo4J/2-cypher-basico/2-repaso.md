# Repaso

Vamos a repetir, pero con una pequeña variación.

```cypher
CREATE (p:Persona {nombre: "Ana", edad: 25})
```

Ejecuta varias veces.

Ahora:

```cypher
MATCH (p:Persona {nombre: "Ana"}) RETURN p
```

Detente.

Hay varias “Ana”.

Esto no es un error. Es exactamente lo que pediste.

Aquí aparece una idea clave: CREATE siempre crea.

### Pensando en el problema

Antes de seguir, piensa en esto:

En SQL, ¿cómo evitarías duplicados?

Probablemente con claves primarias.

Aquí no tienes eso por defecto.

Aquí tú controlas el modelo.

