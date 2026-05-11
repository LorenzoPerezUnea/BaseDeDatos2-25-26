# Embeddings reales con Transformer

### Objetivo

Sustituir la simulación de embeddings por un modelo real ligero basado en transformers, y cerrar el flujo completo:

texto → embedding real → FAISS → búsqueda semántica

### Carga de un modelo real de embeddings

Se utiliza un modelo ligero optimizado para CPU:

SentenceTransformers

```python
from sentence_transformers import SentenceTransformer

model = SentenceTransformer("all-MiniLM-L6-v2")
```

Este modelo convierte frases en vectores densos que capturan significado semántico real.

### Generación de embeddings reales

A partir de este punto, el embedding deja de ser una simulación.

```python
def embedding_real(texto):
    return model.encode(texto).astype("float32")
```

### Comparación conceptual inmediata

Ahora una misma frase tiene representación semántica real:

```python
print(embedding_real("gato rápido"))
print(embedding_real("felino veloz"))
```

Ambos vectores serán cercanos aunque las palabras no coincidan exactamente.

### Reconstrucción de la base con embeddings reales

Se reutiliza la base ya existente:

```python
index.reset()

vectores_real = np.array([embedding_real(t) for t in base])

dim = vectores_real.shape[1]

index = faiss.IndexFlatL2(dim)
index.add(vectores_real)
```

### Búsqueda semántica real con FAISS

```python
def buscar_semantico(query, k=5):
    q = embedding_real(query).reshape(1, -1)

    dist, idx = index.search(q, k)

    return [(base[i], dist[0][j]) for j, i in enumerate(idx[0])]
```

### Ejecución de consultas semánticas

```python
print(buscar_semantico("animal veloz"))
print(buscar_semantico("coche rápido"))
print(buscar_semantico("felino salvaje"))
```

