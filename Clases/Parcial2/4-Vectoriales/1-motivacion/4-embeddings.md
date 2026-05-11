# Introducción a embeddings

Un embedding es simplemente:

una función que convierte texto en vector

Entrada:
"gato"

Salida:
[1.0, 1.0]

Nosotros vamos a construir uno artificial.

### Ejercicio guiado 3: primer embedding simple

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

### Validación del embedding

```python
palabras = ["gato", "felino", "perro", "auto"]

for p in palabras:
    print(p, embedding_simple(p))
```

esto es equivalente a una tabla de representación.

### Ejercicio guiado: medir similitud entre palabras

```python
print("gato-felino:", distancia(embedding_simple("gato"), embedding_simple("felino")))
print("gato-perro:", distancia(embedding_simple("gato"), embedding_simple("perro")))
print("gato-auto:", distancia(embedding_simple("gato"), embedding_simple("auto")))
```

Interpretación guiada:

* menor distancia → más parecido
* mayor distancia → menos parecido

