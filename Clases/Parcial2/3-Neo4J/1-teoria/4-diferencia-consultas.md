# Diferencia clave en la forma de consultar

Aquí es donde ocurre el cambio más importante.

En modelos tradicionales solemos hacer preguntas como:

* dame todos los usuarios con cierta condición
* dame todos los productos de cierta categoría

En grafos, las preguntas cambian a:

* ¿a qué nodos puedo llegar desde aquí?
* ¿qué caminos existen entre dos entidades?
* ¿qué patrones de relaciones aparecen en el grafo?

Este cambio es fundamental. Ya no estamos filtrando registros, estamos recorriendo conexiones.

### Ejercicio conceptual, pensar en caminos

Imagina el siguiente escenario:

```text
(Ana) -> (Luis) -> (Carlos) -> (Marta)
```

Pregunta:

* ¿cómo encontrarías un camino entre Ana y Marta en SQL?
* ¿qué tan natural resulta hacerlo?

Ahora compáralo con la idea de recorrer el grafo paso a paso.

Este tipo de problemas es donde los grafos destacan de forma clara.

### Casos de uso para grafos

Hay problemas donde este modelo no solo es útil, sino casi obligatorio.

Algunos ejemplos reales:

* redes sociales, donde las relaciones son el núcleo
* sistemas de recomendación, donde se buscan conexiones indirectas
* detección de fraude, donde interesa descubrir patrones ocultos
* sistemas de rutas, donde se calculan caminos óptimos
* grafos de conocimiento, donde se conectan conceptos y entidades

En todos estos casos, la relación es tan importante como el dato.

