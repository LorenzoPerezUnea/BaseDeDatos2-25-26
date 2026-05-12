# Conflicto semántico

Agregar frases que mezclan conceptos:

```python
base.append("gato auto rápido")
base.append("perro auto lento")

vectores = [embedding_frase_1(t) for t in base]
```

### Evaluación del conflicto

```python
evaluar_query("auto")
evaluar_query("gato")
```

Las combinaciones híbridas afectan la posición de los resultados.

### Observación del comportamiento emergente

A medida que crece la base:

* aparecen relaciones no previstas
* algunos resultados se vuelven difíciles de interpretar
* el sistema depende cada vez más del diseño del embedding

### Evaluación intensiva de queries

```python
queries = [
    "gato",
    "felino",
    "perro",
    "auto",
    "rápido",
    "lento",
    "banco",
    "banco financiero",
    "banco parque",
    "animal"
]

for q in queries:
    print("\nQuery:", q)
    evaluar_query(q)
```

Este bloque permite observar el comportamiento completo del sistema ante múltiples entradas.

### Interpretación final del comportamiento

El sistema presenta tres características clave:

* responde según la representación vectorial, no según palabras exactas
* es altamente sensible a cómo se define el embedding
* no maneja correctamente ambigüedad sin contexto adicional

Esto muestra que el embedding no solo representa datos, sino que define el comportamiento completo del sistema de búsqueda.


