# Introduciendo patrones más ricos

Vamos a combinar lo aprendido.

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)-[:TRABAJA_EN]->(e:Empresa)
RETURN a.nombre, e.nombre
```

Ejecuta.

Esto es una extensión natural de lo que ya sabes.

### Variación con filtros intermedios

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)-[:TRABAJA_EN]->(e:Empresa)
WHERE b.edad > 30
RETURN a.nombre, e.nombre
```

Aquí estás filtrando en el nodo intermedio.

Esto es algo muy potente en grafos.

### Construyendo una consulta completa

Vamos a juntar varias ideas.

Objetivo:

* Partir de una persona (`Luis`)
* Recorrer amigos de amigos
* Considerar únicamente aquellos que trabajan en alguna empresa
* Agrupar por empresa
* Contar cuántos contactos (a 2 saltos) trabajan en cada una
* Mostrar todas las empresas con al menos un contacto
* Ordenar por número de contactos (descendente)

```cypher
MATCH (a:Persona {nombre: "Luis"})-[:AMIGO_DE]->()-[:AMIGO_DE]->(c)
MATCH (c)-[:TRABAJA_EN]->(e)
WITH e, count(DISTINCT c) AS total, collect(c.nombre) AS personas
RETURN e.nombre, total, personas
ORDER BY total DESC
```

Ejecuta.

Esto ya es una consulta con varias capas.

### Variación para reforzar

Cambia:

* el nodo inicial
* el filtro
* elimina el ORDER BY

Ejecuta varias veces.

Observa cómo cambia el resultado.

### Error típico en consultas complejas

Cuando las consultas crecen, es fácil perder variables.

Si algo falla, revisa:

* qué variables pasan por WITH
* qué variables existen en RETURN

Este tipo de errores son normales.

