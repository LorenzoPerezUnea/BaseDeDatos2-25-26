# Ejercicio final

Construir un flujo completo:

```python
sistema = BuscadorSemantico(base)

sistema.agregar("tren de alta velocidad")
sistema.agregar("elefante africano grande")

print(sistema.buscar("animal"))
print(sistema.buscar("transporte rápido"))
```

### Resultado esperado

El sistema debe:

* integrar nuevos datos
* responder consultas coherentes
* mantener consistencia en resultados

### Resultado de la clase

Se ha construido un sistema que:

* encapsula embeddings y FAISS
* permite inserción de datos
* permite búsqueda configurable
* puede adaptarse a distintos dominios
* está listo para ser extendido

### Preparación directa para el taller

Este sistema será la base del taller:

* se entregará con funciones predefinidas
* se pedirá extenderlo
* se trabajará únicamente en Python

El alumno ya dispone de todas las piezas necesarias para construir una aplicación completa basada en búsqueda semántica.

