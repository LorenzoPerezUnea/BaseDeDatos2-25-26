# Construyendo consultas en etapas

Vamos a hacer algo más completo.

Objetivo:

* contar participantes en proyectos
* filtrar
* ordenar

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:PARTICIPA_EN]->(p:Proyecto)
WITH p, count(b) AS participantes
WHERE participantes > 1
RETURN p.nombre, participantes
ORDER BY participantes DESC
```

Ejecuta.

Esto ya es una consulta real.

### Introduciendo múltiples MATCH

Hasta ahora has usado un solo MATCH.

Vamos a combinar varios.

```cypher
MATCH (a:Persona {nombre: "Luis"})
MATCH (a)-[:AMIGO_DE]->(b:Persona)
MATCH (b)-[:VIVE_EN]->(c:Ciudad)
RETURN a, b, c
```

Ejecuta.

Esto es equivalente a escribir un patrón completo, pero separado.

### Variación: mismo resultado, distinta forma

```cypher
MATCH (a:Persona {nombre: "Luis"})-[:AMIGO_DE]->(b:Persona)-[:VIVE_EN]->(c:Ciudad)
RETURN a, b, c
```

Ambas consultas hacen lo mismo.

Esto es importante: puedes escribir consultas de varias formas.

