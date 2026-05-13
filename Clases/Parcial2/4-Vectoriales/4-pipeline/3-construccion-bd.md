# Construcción de la base de datos

```python
base = [
    "gato doméstico pequeño",
    "perro grande guardián",
    "felino salvaje tigre",
    "coche deportivo rápido",
    "vehículo eléctrico moderno",
    "bicicleta urbana ligera"
]
```

### Qué representa esta base

A diferencia de SQL o grafos:

* no hay esquema
* no hay tipos de datos
* no hay relaciones explícitas

La estructura está implícita en el contenido textual.

### Implicación clave

El sistema no sabe qué es un animal o un vehículo.

Solo sabe cómo se posicionan esos textos en el espacio vectorial.

### Construcción del índice

```python
def construir_indice(base):
    vectores = np.array([embedding(t) for t in base])
    dim = vectores.shape[1]

    index = faiss.IndexFlatL2(dim)
    index.add(vectores)

    return index, vectores
```

### Análisis de esta función

Esta función realiza varias operaciones críticas:

1. genera embeddings para toda la base
2. construye el espacio vectorial
3. crea un índice optimizado para búsqueda
4. almacena los vectores en FAISS

### Justificación del índice

FAISS permite:

* búsquedas rápidas en alta dimensión
* comparación eficiente de vectores
* escalabilidad

Sin FAISS, el sistema sería lento al crecer.

### Ejecución

```python
index, vectores = construir_indice(base)
```



