# Nodos puente

Ahora vamos a ver algo más interesante.

```cypher
MATCH p = (a:Persona)-[:AMIGO_DE*1..3]->(b:Persona)
UNWIND nodes(p) AS n
RETURN n.nombre, count(*) AS apariciones
ORDER BY apariciones DESC
```

Esto cuenta cuántas veces aparece un nodo en caminos.

Esto ya no mide conexiones directas.

Mide presencia en recorridos.

# Interpretando nodos puente

Si un nodo aparece mucho en paths:

* conecta distintas partes del grafo
* actúa como intermediario
* puede ser crítico para la estructura

Esto es mucho más interesante que contar relaciones.


