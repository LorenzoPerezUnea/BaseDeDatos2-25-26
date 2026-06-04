# Error típico y aprendizaje

Es muy probable que al repetir consultas hayas creado nodos duplicados.

Esto es completamente normal.

Ejemplo:

```cypher
CREATE (n:Persona {nombre: "Ana"})
```

Si ejecutas esto varias veces, tendrás varias “Ana”.

Este comportamiento nos enseña algo importante:

Neo4j no impone restricciones automáticamente.

El control del modelo depende de cómo escribimos las consultas.

Más adelante veremos cómo evitar duplicados correctamente.

### Pensando en patrones

Hasta ahora has hecho tres cosas fundamentales:

* crear nodos
* crear relaciones
* consultar patrones

En grafos, las consultas no se basan en condiciones aisladas, sino en patrones de conexión.

Ejemplo:

```cypher
MATCH (a:Persona)-[:AMIGO_DE]->(b:Persona)
RETURN a.nombre, b.nombre
```

Aquí no solo buscamos datos, describimos una forma del grafo.

### Comparación directa con SQL

Recuerda el problema que vimos antes con joins.

Ahora compáralo con esta consulta:

```cypher
MATCH (a)-[:AMIGO_DE]->()-[:AMIGO_DE]->(c)
RETURN a, c
```

Lo que en SQL requería múltiples joins, aquí se expresa de forma directa.

No es solo más corto, es más cercano a cómo pensamos el problema.

### Ejercicio de consolidación

Realiza los siguientes pasos:

1. crea al menos 5 personas
2. conecta las personas formando una red
3. ejecuta una consulta de amigos de amigos
4. observa el resultado como grafo

Después intenta responder:

* ¿qué nodos están más conectados?
* ¿qué caminos aparecen?

Este tipo de observación es clave en bases de datos de grafos.

