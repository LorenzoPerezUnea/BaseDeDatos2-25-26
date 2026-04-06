# Primer contacto con datos

Hasta ahora hemos preparado el entorno y entendido el modelo. A partir de este momento vamos a empezar a trabajar directamente con datos dentro de Neo4j.

Abre la interfaz web y sitúate en el editor de consultas. Todo lo que hagamos a partir de aquí se ejecuta en ese panel.

Vamos a empezar con la operación más simple posible: crear un nodo.

```cypher
CREATE (n:Persona {nombre: "Ana", edad: 25})
```

Ejecuta la consulta y observa qué ocurre. Neo4j no solo guarda el dato, sino que también lo representa visualmente.

Ese pequeño punto que ves en pantalla es un nodo.

### Entendiendo lo que acabas de hacer

Vamos a descomponer la instrucción anterior para entenderla completamente.

* CREATE indica que vamos a crear algo
* (n:Persona) define un nodo con etiqueta Persona
* {nombre: "Ana", edad: 25} son las propiedades

El identificador n es una variable temporal que usamos dentro de la consulta.

Este patrón es la base de todo lo que haremos en Cypher.

### Consultar lo que existe

Ahora vamos a recuperar lo que acabamos de crear.

```cypher
MATCH (n) RETURN n
```

MATCH es el equivalente a buscar. En este caso estamos diciendo: encuentra todos los nodos.

Ejecuta la consulta y observa que aparece el nodo creado anteriormente.

Aquí ya puedes notar una diferencia importante: el resultado no es solo una tabla, también es un grafo.


