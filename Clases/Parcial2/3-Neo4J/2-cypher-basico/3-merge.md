# Introduciendo MERGE como control

Vamos a hacer lo mismo, pero bien.

```cypher
MERGE (p:Persona {nombre: "Laura"})
RETURN p
```

Ejecuta varias veces.

No se duplica.

Ahora añade información:

```cypher
MERGE (p:Persona {nombre: "Laura"})
SET p.edad = 29
RETURN p
```

Ejecuta varias veces.

Observa que no aparecen nuevos nodos.

Aquí estás haciendo algo muy importante: separar identidad de propiedades.

### Variación intencional para entender MERGE

Vamos a provocar un caso interesante.

```cypher
MERGE (p:Persona {nombre: "Laura", edad: 30})
RETURN p
```

Ejecuta.

¿Aparece otro nodo?

Si sí, ya entendiste algo clave: MERGE usa exactamente lo que le das como criterio.

Esto genera muchos errores en alumnos.


