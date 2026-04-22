# Entrando en Cypher

En la clase anterior entendiste qué es un grafo. Hoy vamos a empezar a trabajar con él de verdad, pero con una diferencia importante: no vamos a ejecutar comandos sin pensar, vamos a entender qué estamos construyendo.

Antes de escribir nada, sitúate en Neo4j y asegúrate de tener el panel de consultas listo.

Vamos a empezar con algo extremadamente simple:

```cypher
CREATE (p:Persona {nombre: "Ana", edad: 25})
```

Ejecuta.

Ahora:

```cypher
MATCH (n) RETURN n
```

No avances todavía.

Mira lo que aparece. No es una tabla. Es un nodo dentro de un espacio. Aunque sea uno solo, ya estás dentro de un grafo.

Aquí hay una primera idea importante: en grafos no trabajas con filas, trabajas con entidades.

