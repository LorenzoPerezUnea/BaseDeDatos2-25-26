# Volviendo a embeddings

Recordamos nuestro embedding simple:

```python
def embedding_simple(texto):
    if texto == "gato":
        return np.array([1.0, 1.0])
    elif texto == "felino":
        return np.array([1.1, 1.05])
    elif texto == "perro":
        return np.array([0.9, 1.0])
    elif texto == "auto":
        return np.array([-1.0, -1.0])
    else:
        return np.array([0.0, 0.0])
```

# Ejercicio guiado: comparar con coseno

```python
print("gato-felino:", coseno(embedding_simple("gato"), embedding_simple("felino")))
print("gato-auto:", coseno(embedding_simple("gato"), embedding_simple("auto")))
```

Interpretación:

* valores cercanos a 1 → similares
* valores cercanos a -1 → opuestos

### Construcción de búsqueda con coseno

Ahora reemplazamos distancia por coseno.

```python
base = ["gato", "felino", "perro", "auto"]

def buscar(query):
    q_vec = embedding_simple(query)
    resultados = []

    for item in base:
        vec = embedding_simple(item)
        sim = coseno(q_vec, vec)
        resultados.append((item, sim))

    return sorted(resultados, key=lambda x: x[1], reverse=True)

print(buscar("gato"))
```

### Ejercicio guiado: comparar resultados

Comparar con versión anterior (si la tienes):

* ahora los resultados son más coherentes
* no dependen del tamaño del vector
  

