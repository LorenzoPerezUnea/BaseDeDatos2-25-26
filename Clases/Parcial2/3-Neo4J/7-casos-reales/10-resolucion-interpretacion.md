# Resolución e Interpretación de Ejercicios

### Ejercicio 1

Identificar las empresas que concentran mayor número de conexiones indirectas a través de relaciones sociales.

```cypher
MATCH (a:Persona)-[:AMIGO_DE*1..2]->(b:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN 
  e.nombre AS empresa,
  count(DISTINCT a) AS personas_origen,
  count(DISTINCT b) AS empleados_alcanzados
ORDER BY personas_origen DESC
```

La consulta recorre caminos sociales cortos hasta llegar a personas que trabajan en empresas.

Se utiliza DISTINCT para evitar duplicados y contar cuántas personas diferentes están conectadas indirectamente con cada empresa.

Esto permite identificar qué empresas tienen mayor alcance indirecto dentro de la red.

### Ejercicio 2

Encontrar personas que están conectadas con al menos 2 proyectos distintos a través de sus contactos.

```cypher
MATCH (a:Persona)-[:AMIGO_DE*1..2]->(b:Persona)-[:PARTICIPA_EN]->(pr:Proyecto)
WITH a, count(DISTINCT pr) AS proyectos_conectados
WHERE proyectos_conectados >= 3
RETURN a.nombre, proyectos_conectados
ORDER BY proyectos_conectados DESC
```

Se identifican proyectos a los que una persona no está directamente vinculada, pero a los que accede a través de sus contactos.

El uso de DISTINCT evita contar el mismo proyecto varias veces.

Filtrar la cantidad de proyectos diferentes conectados.

Esto mide exposición indirecta a actividad profesional.

### Ejercicio 3

Detectar ciudades que actúan como puntos de concentración en la red social indirecta.

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
MATCH (b)-[:VIVE_EN]->(c:Ciudad)
RETURN 
  c.nombre AS ciudad,
  count(DISTINCT b) AS personas_alcanzadas,
  count(DISTINCT a) AS personas_origen,
  count(p) AS volumen_paths
ORDER BY personas_alcanzadas DESC
```

Se cuentan paths que terminan en personas distintas que viven en una ciudad.

No se cuentan personas, sino recorridos, lo que mide intensidad de presencia en la red.

Esto permite detectar hubs geográficos.

### Ejercicio 4

Identificar personas que funcionan como nodos puente dentro del grafo.

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
UNWIND nodes(p)[1..-1] AS n
WITH n, count(DISTINCT p) AS apariciones
RETURN n.nombre, apariciones
ORDER BY apariciones DESC
```

Se descomponen los paths en nodos individuales con UNWIND.

Luego se cuentan las apariciones de cada nodo en todos los caminos.

Los nodos con mayor número de apariciones actúan como puentes estructurales.

### Ejercicio 5

Encontrar conexiones entre empresas a través de relaciones sociales fuertes.

```cypher
MATCH p = (a:Persona)-[r:AMIGO_DE*1..3]->(b:Persona)
MATCH (a)-[:TRABAJA_EN]->(e1:Empresa)
MATCH (b)-[:TRABAJA_EN]->(e2:Empresa)
WHERE 
  e1 <> e2 AND 
  ALL(rel IN r WHERE rel.intensidad > 7) AND
  id(e1) < id(e2)
WITH e1, e2, count(DISTINCT b) AS conexiones_fuertes
RETURN e1.nombre, e2.nombre, conexiones_fuertes
ORDER BY conexiones_fuertes DESC
```

Se filtran paths por intensidad, asegurando que solo se consideran relaciones fuertes.

Después se conectan empresas a través de esas relaciones.

Esto revela vínculos sólidos entre organizaciones.

### Ejercicio 6

Detectar posibles inconsistencias donde personas están conectadas a proyectos de empresas distintas a donde trabajan mediante paths.

```cypher
MATCH (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)-[:PARTICIPA_EN]->(pr:Proyecto)
MATCH (pr)-[:PERTENECE_A]->(e:Empresa)
MATCH (a)-[:TRABAJA_EN]->(e2:Empresa)
WHERE e <> e2
WITH a, e, e2, count(DISTINCT pr) AS proyectos_distintos
RETURN 
  a.nombre AS persona,
  e2.nombre AS empresa_trabajo,
  e.nombre AS empresa_proyecto,
  proyectos_distintos
ORDER BY proyectos_distintos DESC
```

o tambien:

```cypher
MATCH (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)-[:PARTICIPA_EN]->(pr:Proyecto)
MATCH (pr)-[:PERTENECE_A]->(e:Empresa)
MATCH (a)-[:TRABAJA_EN]->(e2:Empresa)
WHERE e <> e2
WITH 
  a, 
  e, 
  e2, 
  count(DISTINCT pr) AS proyectos,
  collect(DISTINCT pr.nombre) AS lista_proyectos
RETURN 
  a.nombre,
  e2.nombre AS trabaja_en,
  e.nombre AS proyectos_en,
  proyectos,
  lista_proyectos
ORDER BY proyectos DESC
```

Se detectan situaciones donde una persona, a través de la red, está conectada con proyectos de empresas distintas a la suya.

Esto puede indicar:

* colaboración externa
* movilidad laboral
* inconsistencias en el modelo

El conteo de paths mide cuán fuerte es esa conexión indirecta.

