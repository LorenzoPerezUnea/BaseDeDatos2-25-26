# Ejercicios integradores con FAISS y SentenceTransformers

### Objetivo operativo

En esta parte no se introduce teoría nueva, se consolida todo lo aprendido en un único flujo operativo.

El objetivo es construir una base técnica que ya tenga forma de sistema real, no de experimento.

Este sistema será reutilizado directamente en el taller, por lo que cada función debe entenderse como una pieza estable, no como código temporal.

### Cambio de enfoque respecto a clases anteriores

Hasta ahora:

* se probaban ideas
* se analizaban comportamientos
* se observaban resultados

A partir de aquí:

* se construyen funciones reutilizables
* se separan responsabilidades
* se organiza el código como sistema

Esto es un cambio importante: se pasa de exploración a construcción.

### Estructura que se va a construir

Durante esta parte se implementa una arquitectura mínima pero completa:

```text
datos (base de textos)
↓
función de embedding
↓
generación de vectores
↓
construcción de índice FAISS
↓
función de búsqueda
```

Cada elemento tiene un rol claro y no se mezcla con otros.


