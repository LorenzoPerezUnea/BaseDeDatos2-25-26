# Inserción incremental (dinámica)

FAISS permite añadir nuevos vectores sin reconstruir el índice.

```python
nuevo_texto = "gato salvaje rápido"
nuevo_vector = embedding_frase_1(nuevo_texto).astype("float32").reshape(1, -1)

index.add(nuevo_vector)

id_to_texto[index.ntotal - 1] = nuevo_texto
```

### Búsqueda después de inserción

```python
print(buscar_faiss("felino rápido"))
```

### Comparación conceptual con sistema manual

Antes:

* búsqueda sobre listas
* comparación en Python
* ordenamiento manual

Ahora:

* búsqueda en índice optimizado
* cálculo en C++ interno
* retorno directo de vecinos

### Qué NO hace FAISS

Es importante entender lo que FAISS no hace:

* no genera embeddings
* no entiende texto
* no decide significado

Solo:

* almacena vectores
* acelera búsqueda de vecinos

### Qué sí aporta FAISS

* reducción drástica de tiempo de consulta
* escalabilidad a millones de vectores
* abstracción del problema de búsqueda

### Inserción + búsqueda como sistema completo

```text
texto → embedding → FAISS.add()
consulta → embedding → FAISS.search() → resultados
```

### Relación con sistemas RAG

En sistemas de recuperación aumentada:

```text
documentos → embeddings → FAISS
query → embedding → FAISS → contexto → LLM
```

FAISS actúa como capa de memoria estructurada.

### Limitación del índice actual

El índice usado (`IndexFlatL2`) sigue siendo exacto:

* escala mejor que Python puro
* pero no reduce complejidad asintótica

Esto abre la puerta a índices aproximados (IVF, HNSW), que se verán en fases posteriores.

### Cambio conceptual

El sistema ahora ya no es una lista ni una simulación:

es una base de datos vectorial funcional con inserción y consulta directa.

El siguiente paso natural es entender cómo estos índices se vuelven aproximados para escalar a millones de vectores sin perder calidad significativa en los resultados.


