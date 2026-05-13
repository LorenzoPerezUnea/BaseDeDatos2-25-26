# Índices reales

Los sistemas modernos no usan diccionarios manuales, sino estructuras como:

* clustering automático
* grafos de vecindad
* particiones dinámicas del espacio

Estas estructuras se construyen directamente sobre embeddings.

### FAISS como implementación real

FAISS permite construir estos índices de forma eficiente.

Su funcionamiento se basa en:

* agrupar vectores similares
* reducir candidatos de búsqueda
* aproximar vecinos cercanos sin comparar todo

### Diferencia clave con el sistema construido

Sistema manual:

* reglas explícitas
* categorías fijas
* lógica determinista

Sistema real:

* agrupación basada en geometría
* sin etiquetas humanas
* optimización estadística

### Cambio conceptual

El problema deja de ser:

“cómo comparo vectores”

y pasa a ser:

“cómo organizo el espacio para no tener que comparar todos los vectores”

