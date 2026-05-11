# Introduciendo paths válidos vs inválidos

Piensa en esto:

un path puede existir, pero no ser relevante.

Ejemplo:

* conexiones débiles
* pasos irrelevantes
* nodos intermedios sin sentido

Aquí es donde empiezas a filtrar calidad.

### Introduciendo paths simples (evitar ciclos)

```cypher
MATCH p = (a:Persona)-[r:AMIGO_DE*1..4]->(b:Persona)
WHERE ALL(n IN nodes(p) WHERE single(x IN nodes(p) WHERE x = n))
RETURN a, b, r
```

Esto evita repetir nodos en el camino.

Evita ciclos.

### Observando el impacto

Ejecuta con y sin ese filtro.

Vas a ver:

* menos resultados
* más coherencia

### Introduciendo paths más relevantes

Vamos a combinar varias ideas.

```cypher
MATCH p = (a:Persona)-[r:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
WHERE ALL(rel IN r WHERE rel.intensidad > 5)
RETURN a.nombre, e.nombre, length(p)
ORDER BY length(p) ASC
```

Aquí estás diciendo:

solo caminos fuertes y cortos.

### Introduciendo caminos alternativos

Un mismo par de nodos puede tener múltiples paths.

```cypher
MATCH p = (a:Persona {nombre: "Ana"})-[:AMIGO_DE*1..3]->(b:Persona)
RETURN b.nombre, count(p)
```

Esto cuenta cuántos caminos existen.

