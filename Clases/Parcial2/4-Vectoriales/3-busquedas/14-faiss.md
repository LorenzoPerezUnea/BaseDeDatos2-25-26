# Inserción y búsqueda directa con FAISS

El foco está en pasar de estructuras simuladas a un flujo real de indexación y consulta.

### Preparación del entorno FAISS

FAISS trabaja con arrays de tipo `float32`, por lo que los vectores deben adaptarse a ese formato.

```yml
version: "3.9"

services:
  vector-db-class:
    image: python:3.11-slim
    container_name: vector_db_class
    ports:
      - "8888:8888"
    volumes:
      - ./notebooks:/app
    working_dir: /app

    command: >
      bash -c "
      pip install --no-cache-dir numpy notebook ipykernel faiss-cpu sentence-transformers &&
      python -m ipykernel install --user &&
      jupyter notebook
      --ip=0.0.0.0
      --port=8888
      --no-browser
      --allow-root
      --ServerApp.token=1234
      "
```

```python
import numpy as np
import faiss
```

### Conversión de embeddings al formato FAISS

FAISS requiere matrices 2D con tipo float32.

```python
def preparar_vectores(vectores):
    return np.array(vectores).astype("float32")
```

### Creación del índice vectorial

Se crea un índice básico de tipo búsqueda exacta (Flat L2).

```python
dimension = 4

index = faiss.IndexFlatL2(dimension)
```

Este tipo de índice:

* no comprime datos
* no aproxima resultados
* compara contra todos los vectores internamente, pero optimizado en C++

### Inserción de vectores en el índice

Los vectores de la base se insertan directamente en FAISS.

```python
vectores_np = preparar_vectores(vectores)

index.add(vectores_np)

print("Vectores en índice:", index.ntotal)
```

### Cómo funciona la inserción

FAISS no guarda textos, solo vectores.

La relación texto-vector se mantiene externamente:

```python
id_to_texto = {i: base[i] for i in range(len(base))}
```

### Consulta directa en FAISS

Se convierte la query a vector y se busca en el índice.

```python
def buscar_faiss(query, k=5):
    q_vec = embedding_frase_1(query).astype("float32").reshape(1, -1)

    distancias, indices = index.search(q_vec, k)

    resultados = []

    for i in indices[0]:
        resultados.append(id_to_texto[i])

    return resultados
```

### Ejecución de búsqueda

```python
print(buscar_faiss("gato rápido"))
```

### Qué devuelve FAISS realmente

FAISS devuelve:

* índices de los vectores más cercanos
* distancias asociadas

```python
q_vec = embedding_frase_1("auto rápido").astype("float32").reshape(1, -1)

distancias, indices = index.search(q_vec, 5)

print(indices)
print(distancias)
```

### Interpretación de distancias

En `IndexFlatL2`:

* valores más pequeños = más cercanos
* representa distancia euclidiana

