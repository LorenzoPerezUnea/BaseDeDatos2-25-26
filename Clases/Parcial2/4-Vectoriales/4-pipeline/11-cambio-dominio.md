# Cambio de dominio

Reemplazar completamente la base:

```python
base_comida = [
    "pizza italiana",
    "hamburguesa americana",
    "sushi japonés",
    "tacos mexicanos",
    "pasta con salsa"
]

sistema = BuscadorSemantico(base_comida)

print(sistema.buscar("comida asiática"))
```

### Qué se demuestra

El sistema es independiente del dominio.

Solo necesita:

* textos
* embeddings

### Extensión del sistema

Agregar funcionalidad nueva:

```python
class BuscadorSemantico:

    def __init__(self, base):
        self.base = base
        self.index, self.vectores = construir_indice(base)

    def buscar(self, query, k=3):
        return buscar_con_score(query, self.base, self.index, k)

    def agregar(self, texto):
        self.base.append(texto)
        self.index, self.vectores = construir_indice(self.base)

    def buscar_filtrado(self, query, umbral=0.5):
        resultados = self.buscar(query)
        return [r for r in resultados if r["score"] > umbral]
```

### Ejecución

```python
sistema = BuscadorSemantico(base)

print(sistema.buscar_filtrado("animal", 0.6))
```

### Qué se busca con este ejercicio

* modificar comportamiento interno
* añadir lógica propia
* preparar el sistema para el taller

### Ejercicio final de preparación

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

