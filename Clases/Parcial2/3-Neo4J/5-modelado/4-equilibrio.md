# Encontrando el equilibrio

Un buen modelo de grafo:

* usa nodos para entidades reales
* usa relaciones para conexiones reales
* usa propiedades para atributos

Ejemplo correcto en tu dataset:

```cypher
MATCH (p:Persona)-[t:TRABAJA_EN]->(e:Empresa)
MATCH (p)-[v:VIVE_EN]->(c:Ciudad)
RETURN p, e, c, t, v
```

Aquí todo tiene sentido semántico.

### Introduciendo dirección en relaciones

Otro punto crítico.

¿Debe ser dirigida una relación?

Ejemplo:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a, b
```

Pregunta:

¿la amistad es direccional?

En muchos casos, no.

Pero en el modelo sí lo es.

Esto implica que tú decides cómo interpretarla.

### Variación: ignorando dirección

```cypher
MATCH (a:Persona)-[:AMIGO_DE]-(b:Persona)
RETURN a, b
```

Esto cambia completamente el comportamiento.

### Introduciendo semántica en relaciones

Una relación no es solo conexión.

Es significado.

Ejemplo:

```cypher
MATCH (p:Persona)-[r:TRABAJA_EN]->(e:Empresa)
RETURN p.nombre, e.nombre, r.rol
```

La relación tiene información relevante.

Esto es modelado correcto.

### Ejercicio guiado

Toma este escenario:

personas, empresas y ciudades

Objetivo:

encontrar personas que trabajan en una ciudad distinta a donde viven

```cypher
MATCH (p:Persona)-[t:TRABAJA_EN]->(e:Empresa)
MATCH (p)-[v:VIVE_EN]->(c:Ciudad)
RETURN p, e, c, t, v
```

```cypher
MATCH (e1:Empresa {nombre: "TechCorp"}), (c1:Ciudad {nombre: "Madrid"})
CREATE (e1)-[:UBICADA_EN]->(c1);

MATCH (e2:Empresa {nombre: "FinBank"}), (c2:Ciudad {nombre: "Barcelona"})
CREATE (e2)-[:UBICADA_EN]->(c2);

MATCH (e3:Empresa {nombre: "HealthPlus"}), (c3:Ciudad {nombre: "Valencia"})
CREATE (e3)-[:UBICADA_EN]->(c3);
```

Modifica la consulta para detectar diferencias.

```cypher
MATCH (p:Persona)-[t:TRABAJA_EN]->(e:Empresa)-[:UBICADA_EN]->(cTrabajo:Ciudad)
MATCH (p)-[v:VIVE_EN]->(cVive:Ciudad)
WHERE cTrabajo <> cVive
RETURN 
  p.nombre AS persona,
  cVive.nombre AS vive_en,
  cTrabajo.nombre AS trabaja_en,
  t.rol
ORDER BY persona
```

o también:

```cypher
MATCH (p:Persona)-[t:TRABAJA_EN]->(e:Empresa)-[:UBICADA_EN]->(cTrabajo:Ciudad)
MATCH (p)-[:VIVE_EN]->(cVive:Ciudad)
WHERE cTrabajo <> cVive
RETURN 
  p.nombre,
  cVive.nombre AS vive_en,
  cTrabajo.nombre AS trabaja_en,
  e.nombre AS empresa,
  t.rol
ORDER BY cTrabajo.nombre
```

vista de grafo:

```cypher
MATCH (p:Persona)-[t:TRABAJA_EN]->(e:Empresa)-[u:UBICADA_EN]->(cTrabajo:Ciudad)
MATCH (p)-[v:VIVE_EN]->(cVive:Ciudad)
WHERE cTrabajo <> cVive
RETURN  p,  cVive,  cTrabajo,  e,   t,  u,  v
```



