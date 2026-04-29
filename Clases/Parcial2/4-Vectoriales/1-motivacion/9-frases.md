# Paso siguiente: frases en lugar de palabras

Vamos a construir un embedding más interesante.

```python
def embedding_frase(texto):
    palabras = texto.lower().split()
    vector = np.zeros(3)

    for p in palabras:
        if p in ["gato", "felino"]:
            vector += np.array([1, 0, 0])
        elif p in ["perro"]:
            vector += np.array([0.9, 0, 0])
        elif p in ["auto"]:
            vector += np.array([0, 1, 0])
        else:
            vector += np.array([0, 0, 1])

    return vector
```

# Ejercicio guiado: probar frases

```python
t1 = embedding_frase("gato felino")
t2 = embedding_frase("perro")
t3 = embedding_frase("auto")

print("t1-t2:", coseno(t1, t2))
print("t1-t3:", coseno(t1, t3))
```

# Construcción de buscador semántico básico

```python
def coseno(a, b):
    norm_a = np.linalg.norm(a)
    norm_b = np.linalg.norm(b)

    if norm_a == 0 or norm_b == 0:
        return 0  # o -1 según criterio

    return np.dot(a, b) / (norm_a * norm_b)
```

```python

def embedding_frase(texto):
    palabras = texto.lower().split()
    vector = np.zeros(4)

    for p in palabras:
        if p in ["gato", "felino"]:
            vector += np.array([1, 0, 0, 0])
        elif p in ["perro"]:
            vector += np.array([0, 1, 0, 0])
        elif p in ["auto"]:
            vector += np.array([0, 0, 1, 0])
        elif p in ["pequeño", "grande", "salvaje", "rápido"]:
            vector += np.array([0, 0, 0, 1])

    return vector
```

```python
base = [
    "gato pequeño",
    "perro grande",
    "auto rápido",
    "felino salvaje"
]

vectores = [embedding_frase(t) for t in base]

print(vectores)

def buscar(query):
    q_vec = embedding_frase(query)
    print(q_vec)
    resultados = []

    for texto, vec in zip(base, vectores):
        similitud = coseno(q_vec, vec)
        resultados.append((texto, similitud))
    
    print(resultados)

    return sorted(resultados, key=lambda x: x[1], reverse=True)

print(buscar("gato"))
```

