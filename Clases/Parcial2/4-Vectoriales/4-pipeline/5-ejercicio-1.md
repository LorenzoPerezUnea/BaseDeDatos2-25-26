# Ejercicio 1 – Expansión de la base

```python
base.extend([
    "camión de carga pesado",
    "león salvaje africano",
    "motocicleta deportiva"
])

index, vectores = construir_indice(base)
```

### Qué se busca con este ejercicio

* observar cómo cambia el espacio vectorial
* comprobar cómo nuevos elementos afectan resultados
* entender que el sistema es dinámico

### Ejercicio 2 – Variación de consultas

```python
print(buscar("animal salvaje", base, index))
print(buscar("transporte urbano", base, index))
```

### Qué analizar

* cómo pequeñas variaciones cambian el embedding
* cómo cambia el ranking
* cómo responde el sistema a distintos contextos

### Punto clave de esta parte

Se ha construido un sistema completo que:

* transforma texto en vectores
* organiza datos en un espacio geométrico
* permite búsquedas semánticas
* está listo para ser extendido en el taller

Este sistema ya no es experimental.

Es una base funcional sobre la que se puede construir una aplicación real.


