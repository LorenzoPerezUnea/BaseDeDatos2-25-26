# Retomando desde el análisis

En la primera parte empezaste a usar Cypher no solo para consultar, sino para analizar. Ya viste conteos, ordenaciones y cómo extraer información útil del grafo.

Ahora vamos a avanzar hacia algo más potente: construir consultas que se componen en varias etapas.

Antes de escribir nada nuevo, vuelve a situarte.

```cypher
MATCH (n) RETURN n
```

Mira el grafo.

Todo lo que hagamos ahora parte de aquí.

### Pensando en pasos intermedios

Hasta ahora has escrito consultas “de una sola pieza”. Pero en problemas reales necesitas dividir el pensamiento en pasos.

Vamos a empezar con algo sencillo:

quiero obtener personas y cuántos amigos tienen, pero luego quedarme solo con las que tienen más de 1.

Primero:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a.nombre AS nombre, count(b) AS amigos
```

Ejecuta.

Ahora piensa: ¿cómo filtrarías esto?

Muchos intentan hacerlo directamente en WHERE, pero eso no funciona con agregaciones.


