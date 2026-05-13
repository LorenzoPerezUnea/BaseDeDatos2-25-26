# Inicialización del entorno

```python
import numpy as np
import faiss
from sentence_transformers import SentenceTransformer

model = SentenceTransformer("all-MiniLM-L6-v2")
```

Este paso define el tipo de sistema que se está construyendo:

* no se diseñan embeddings manualmente
* se utiliza un modelo entrenado
* el espacio vectorial ya está definido externamente

### Qué implica usar un modelo preentrenado

El modelo introduce propiedades que no se controlan directamente:

* relaciones semánticas aprendidas
* agrupación automática de conceptos
* sensibilidad al contexto lingüístico

Esto significa que el comportamiento del sistema dependerá en gran parte del modelo.

### Definición de la función de embedding

```python
def embedding(texto):
    return model.encode(texto).astype("float32")
```

### Justificación de esta función

Esta función es el punto más crítico del sistema:

* define cómo se representa el significado
* transforma texto en coordenadas
* determina la geometría del espacio

Si esta función cambia, todo el sistema cambia.

### Propiedad importante

Dos textos similares producirán vectores cercanos.

Dos textos diferentes producirán vectores alejados.

El sistema no compara palabras, compara posiciones en el espacio.


