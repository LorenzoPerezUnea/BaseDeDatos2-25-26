# Tipos de estructuras internas

Sin entrar en implementación avanzada, los sistemas vectoriales suelen usar:

* particiones del espacio (clustering)
* grafos de navegación
* árboles de búsqueda aproximada

Todos comparten la misma idea:

no recorrer todo el espacio, sino navegarlo.

### Relación con sistemas RAG

En sistemas de recuperación aumentada:

```text
documentos → embeddings → índice vectorial → búsqueda → contexto para LLM
```

La eficiencia del sistema depende directamente del índice, no del modelo de lenguaje.

### Cambio conceptual importante

Hasta ahora se ha trabajado con:

* representación (embeddings)
* similitud (coseno)
* búsqueda exhaustiva

A partir de este punto, el foco cambia:

cómo estructurar el espacio para no tener que comparar todo con todo

El siguiente paso es ver cómo estas ideas se implementan de forma práctica en sistemas reales utilizando librerías como FAISS, y cómo cambia el comportamiento cuando se introduce indexación real sobre los mismos vectores ya construidos.

