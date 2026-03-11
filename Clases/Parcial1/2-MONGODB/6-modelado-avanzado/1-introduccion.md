# Profundizando en explain() y executionStats

Hasta ahora hemos usado `explain("executionStats")` principalmente para observar:

* COLLSCAN
* IXSCAN
* totalDocsExamined
* totalKeysExamined

Pero explain es mucho más que eso.

Cuando ejecutamos:

```JS
db.cursos.find({ nivel: "avanzado" }).explain("executionStats")
```

MongoDB no solo nos dice qué hizo.
Nos revela cómo tomó decisiones internas.

El resultado contiene tres niveles importantes:

1. queryPlanner
2. executionStats
3. allPlansExecution (en ciertos modos)

### queryPlanner: la decisión estratégica

Dentro de `queryPlanner` encontramos:

* winningPlan
* rejectedPlans
* parsedQuery

Aquí MongoDB nos muestra qué índice eligió y cuáles descartó.

Esto es crucial cuando existen múltiples índices posibles.

Ejemplo conceptual:

```JSO
{
  "winningPlan": { "stage": "IXSCAN" },
  "rejectedPlans": [
     { "stage": "COLLSCAN" }
  ]
}
```

Esto significa que MongoDB evaluó alternativas.

Aquí podemos introducir una pregunta interesante para la clase:

> ¿Qué ocurre si tengo dos índices que podrían resolver la consulta?

MongoDB evalúa costos estimados y elige el plan “más barato”.

### executionStats: lo que realmente ocurrió

Aquí vemos:

* executionTimeMillis
* totalDocsExamined
* totalKeysExamined
* nReturned

Este bloque responde a la pregunta:

> ¿Cuánto trabajo real hizo el motor?

Por ejemplo:

```JS
{
  "nReturned": 3,
  "totalDocsExamined": 100000,
  "totalKeysExamined": 3
}
```

Esto podría indicar un índice ineficiente o un filtro posterior costoso.

### Interpretación profesional

No basta con ver IXSCAN.

Hay que analizar:

* ¿Docs examinados ≈ docs retornados?
* ¿Keys examinadas es razonable?
* ¿El tiempo es coherente con el volumen?

La optimización profesional no es binaria (índice sí / índice no).
Es cuantitativa.

