# Cómo se ve esto en sistemas reales

### Dimensionalidad en entornos empresariales

En los ejercicios anteriores se trabajó con 3 o 4 dimensiones para facilitar la comprensión. En sistemas reales, el número de dimensiones es mucho mayor.

En entornos empresariales con búsqueda vectorial usando FAISS, lo habitual es:

* 384 dimensiones en modelos ligeros
* 768 dimensiones en modelos estándar
* 1024 o más en sistemas más complejos

Esto no es arbitrario. Más dimensiones permiten capturar más matices del lenguaje, pero también implican:

* mayor coste computacional
* mayor uso de memoria
* más dificultad para interpretar resultados

### Qué representa realmente una dimensión

En los ejemplos de clase, cada dimensión tenía un significado claro:

* animal
* vehículo
* velocidad

En sistemas reales, esto deja de ser cierto.

Una dimensión individual no representa un concepto interpretable. En su lugar:

* cada dimensión captura patrones estadísticos del lenguaje
* el significado está distribuido en todo el vector

No se puede interpretar una coordenada aislada. Solo el vector completo tiene sentido.

### Qué se estaba simulando en la clase 2

Cuando se hacían operaciones como:

* cambiar pesos
* mover conceptos
* añadir dimensiones

se estaba simulando manualmente lo que un modelo real aprende automáticamente.

En un sistema real:

* el modelo decide dónde colocar cada término
* los vectores emergen del entrenamiento
* las relaciones no se programan explícitamente

### Cómo se entrenan embeddings en la práctica

Los embeddings utilizados en empresa no se definen manualmente. Se obtienen mediante modelos previamente entrenados.

La idea central del entrenamiento es:

* acercar textos con significado similar
* alejar textos con significado distinto

Ejemplo conceptual:

```text
("gato pequeño", "felino doméstico") → cercanos
("gato pequeño", "motor industrial") → lejanos
```

El modelo ajusta el espacio vectorial para reflejar estas relaciones.

### Tipo de modelos utilizados

La mayoría de embeddings modernos se basan en arquitecturas tipo BERT o variantes optimizadas.

En la práctica empresarial:

* no se entrenan desde cero
* se utilizan modelos preentrenados
* opcionalmente se ajustan (fine-tuning) con datos propios

### Qué hace realmente una empresa

En un sistema típico:

1. Se selecciona un modelo de embeddings
2. Se transforman documentos a vectores
3. Se almacenan en un índice vectorial
4. Se buscan vectores similares ante una consulta

El flujo es:

```text
texto → embedding → almacenamiento → búsqueda
```

### Rol de FAISS en el sistema

FAISS no crea embeddings.

Su función es:

* almacenar vectores
* permitir búsquedas eficientes
* evitar comparar todos contra todos

Esto es clave porque en sistemas reales:

* puede haber millones de vectores
* la búsqueda directa sería inviable

### Separación de responsabilidades

Un sistema vectorial real tiene tres componentes distintos:

* modelo de embedding → define significado
* índice vectorial → permite búsqueda rápida
* sistema superior (como un LLM) → interpreta resultados

### Relación con sistemas RAG

En sistemas de recuperación aumentada (RAG), el flujo completo es:

```text
documentos → embeddings → índice vectorial
consulta → embedding → búsqueda → resultados relevantes
```

Los resultados encontrados se utilizan posteriormente para generar respuestas.

### Problemas reales que no se veían en clase 2

Los ejercicios anteriores eran pequeños y controlados. En sistemas reales aparecen nuevas limitaciones:

* no se puede comparar contra todos los vectores
* el tiempo de respuesta es crítico
* la memoria es limitada
* la precisión compite con la velocidad
  

### Conexión con el siguiente paso

Hasta ahora se ha trabajado sobre:

* cómo se construye el significado
* cómo se representan los datos

El siguiente problema es distinto:

cómo buscar eficientemente dentro de miles o millones de vectores

El embedding define el espacio, pero el índice define si ese espacio se puede usar en la práctica.

