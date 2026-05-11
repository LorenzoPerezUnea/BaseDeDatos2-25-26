# Introduciendo variables de relación en paths

Vamos a capturar relaciones explícitamente.

```cypher
MATCH (a)-[r:AMIGO_DE]->(b)
RETURN r.intensidad
```

Esto ya lo conoces.

Pero ahora piensa: en recorridos largos necesitas controlar cada paso.

### Introduciendo patrones más expresivos

Vamos a construir algo más rico.

```cypher
MATCH (a:Persona)-[r1:AMIGO_DE]->(b:Persona)-[r2:AMIGO_DE]->(c:Persona)
WHERE r1.intensidad > 5 AND r2.intensidad > 5
RETURN a.nombre, c.nombre
```

Ejecuta.

Esto ya es una consulta con condiciones en múltiples niveles.

### Variación: cambiando condiciones

Ahora cambia:

* solo r1
* solo r2
* ambos

Ejecuta cada caso.

Observa cómo cambia el resultado.

por ejemplo:

```cypher
MATCH (a:Persona)-[r1:AMIGO_DE]->(b:Persona)-[r2:AMIGO_DE]->(c:Persona)
MATCH (c)-[:TRABAJA_EN]->(e:Empresa)
MATCH (a)-[:VIVE_EN]->(ci:Ciudad)
WHERE
r1.intensidad > 5 AND
r2.intensidad > 5 AND
a <> c AND
c.edad >= 30 AND
e.sector = "Finanzas"
RETURN
a.nombre AS origen,
c.nombre AS recomendado,
e.nombre AS empresa,
ci.nombre AS ciudad_origen,
(r1.intensidad + r2.intensidad) AS fuerza_red
ORDER BY fuerza_red DESC
```

Aquí estás aprendiendo cómo afecta cada parte del patrón.

