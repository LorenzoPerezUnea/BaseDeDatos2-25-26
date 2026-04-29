# Comparando estilos de escritura

Dos formas:

Separado:

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
return a, e
```

Unificado:

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)-[:TRABAJA_EN]->(e:Empresa)
return a, e
```

Ambas son válidas.

Pero la primera permite más control.

### Introduciendo WITH para controlar paths

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
WITH a, b, length(p) AS distancia
WHERE distancia <= 2
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre, e.nombre, distancia
ORDER BY distancia DESC
```

Esto es clave:

primero recorres, luego filtras, luego continúas

### Introduciendo ranking básico por distancia

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre, e.nombre, length(p) AS distancia
ORDER BY distancia ASC
```

Ahora puedes priorizar conexiones más cercanas.

