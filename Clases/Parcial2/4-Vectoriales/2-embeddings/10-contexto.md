# Ambigüedad, contexto y comportamiento emergente

### Construcción de un conjunto de datos

Se define una base de frases que contienen distintos tipos de conceptos y combinaciones.

```python
base = [
    "gato rápido",
    "perro lento",
    "auto rápido",
    "coche lento",
    "banco financiero",
    "banco parque"
]
```

### Generación de embeddings

```python
vectores = [embedding_frase_1(t) for t in base]

for texto, vec in zip(base, vectores):
    print(texto, vec)
```

Cada frase queda representada como un punto en el espacio vectorial.

### Comparación global entre todos los elementos

```python
for i in range(len(base)):
    for j in range(len(base)):
        sim = coseno(vectores[i], vectores[j])
        print(base[i], "vs", base[j], "→", sim)
```

Este bloque permite observar todas las relaciones internas del sistema.

### Interpretación del comportamiento

Se pueden identificar patrones:

* frases con palabras comunes tienden a ser similares
* frases con estructuras distintas se separan
* ciertas combinaciones generan similitudes inesperadas

