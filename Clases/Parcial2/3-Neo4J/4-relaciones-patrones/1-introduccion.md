# Cambiando el foco: la relación como entidad principal

Hasta ahora has trabajado con nodos y relaciones, pero de forma bastante equilibrada. En esta clase vamos a cambiar el foco: vamos a empezar a tratar las relaciones como algo que también tiene información, no solo como un “conector”.

Antes de escribir nada, observa tu grafo.

```cypher
MATCH (a)-[r]->(b)
RETURN a, r, b
```

Mira las relaciones.

Hasta ahora solo tienen un tipo, como AMIGO\_DE, pero no tienen más información.

En muchos sistemas reales esto no es suficiente.

Piensa en esto:

* no es lo mismo un amigo reciente que uno de hace 10 años
* no es lo mismo una relación fuerte que una débil
* no es lo mismo trabajar en una empresa hoy que haber trabajado antes

Eso significa que la relación también necesita propiedades.


