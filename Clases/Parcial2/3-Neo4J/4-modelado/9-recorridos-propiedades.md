# Limitando recorridos por propiedades

Queremos recorrer solo relaciones “fuertes”.

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e)
WHERE r.intensidad > 6
RETURN a, b, e, r
```

Esto funciona para un salto.

Pero ahora piensa: ¿cómo aplicar eso en múltiples niveles?

Aquí es donde muchos alumnos se bloquean.

### Estrategia: descomponer el recorrido

En lugar de escribir todo en una sola línea, vamos a dividir el problema.

```cypher
MATCH (a:Persona)-[r1:AMIGO_DE]->(b:Persona)
WHERE r1.intensidad > 6
MATCH (b)-[r2:AMIGO_DE]->(c:Persona)
MATCH (c)-[r3:VIVE_EN]->(ci:Ciudad)
WHERE r2.intensidad > 6
RETURN a, c, ci, r1, r2, r3
```

Ejecuta.

Esto simula un recorrido de dos niveles con condiciones.

### Variación: comparando con recorrido automático

Ahora compáralo con:

```cypher
MATCH (a:Persona)-[r:AMIGO_DE*2]->(c:Persona)
RETURN a, c, r
```

Observa la diferencia.

En el segundo caso no puedes controlar propiedades intermedias.

Esto es una limitación importante de los paths automáticos.

### Control manual vs automático

Haz una pausa.

Tienes dos formas de recorrer:

* automático: más corto
* manual: más control

Elegir bien depende del problema.

