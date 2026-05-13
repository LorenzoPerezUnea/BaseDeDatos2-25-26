# Búsqueda lineal como baseline real

### Base

```python
import numpy as np

def embedding_palabra(p):
    if p in ["gato", "felino"]:
        return np.array([1, 0, 0, 0])
    elif p == "perro":
        return np.array([0.8, 0.2, 0, 0])
    elif p in ["auto", "coche"]:
        return np.array([0, 0, 1, 0])
    elif p == "rápido":
        return np.array([0, 0, 0, 1])
    elif p == "lento":
        return np.array([0, 0, 0, -1])
    else:
        return np.zeros(4)

def embedding_frase_1(texto):
    vector = np.zeros(4)
    for palabra in texto.lower().split():
        vector += embedding_palabra(palabra)
    return vector

def coseno(a, b):
    norm_a = np.linalg.norm(a)
    norm_b = np.linalg.norm(b)

    if norm_a == 0 or norm_b == 0:
        return 0

    return np.dot(a, b) / (norm_a * norm_b)
```

### Construcción de una base de datos vectorial

Se comienza construyendo una colección de textos controlada. No se busca realismo lingüístico, sino poder controlar el tamaño y observar el comportamiento del sistema.

```python
base = []

animales = ["gato", "perro", "felino"]
objetos = ["auto", "coche"]
atributos = ["rápido", "lento"]

for a in animales:
    for b in atributos:
        base.append(f"{a} {b}")

for o in objetos:
    for b in atributos:
        base.append(f"{o} {b}")

print(len(base))
print(base[:10])
```

En este punto:

* la base es pequeña
* contiene combinaciones repetibles
* permite entender fácilmente los resultados

### Escalado artificial del volumen de datos

Para simular un entorno más realista, se multiplica la base.

```python
base = base * 500

print(len(base))
```

Aquí no se añade información nueva, pero sí se incrementa el número de elementos.

Esto permite observar cómo afecta el tamaño al rendimiento sin cambiar el contenido semántico.

### Generación de embeddings para toda la base

Cada texto se transforma en un vector.

```python
vectores = [embedding_frase_1(t) for t in base]

print(len(vectores))
print(vectores[0])
```

En este punto:

* cada elemento tiene su representación numérica
* ya no se trabaja con texto directamente
* la búsqueda se hará sobre vectores

### Implementación de búsqueda lineal

Se define el método más simple posible: comparar contra todos.

```python
def buscar_lineal(query):
    q_vec = embedding_frase_1(query)
    resultados = []

    for texto, vec in zip(base, vectores):
        sim = coseno(q_vec, vec)
        resultados.append((texto, sim))

    return sorted(resultados, key=lambda x: x[1], reverse=True)
```

Este enfoque hace exactamente lo siguiente:

1. convierte la query en vector
2. recorre todos los elementos
3. calcula similitud uno a uno
4. ordena los resultados

No hay optimización, ni índices, ni filtrado.

