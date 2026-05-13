# Experimentos

Probar múltiples queries:

```python
print(buscar("felino"))
print(buscar("animal"))
print(buscar("auto"))
print(buscar("perro grande"))
```

modificar reglas del embedding:

* agregar nuevas palabras
* cambiar pesos

```python
def actualizar_vectores(base):
    return [embedding_frase(t) for t in base]
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
        elif p in ["banco"]:
            vector += np.array([0.5, 0.5, 0, 0])  # NUEVO CASO
        else:
            vector += np.array([0.01, 0.01, 0.01, 0.01])

    return vector
```

```python
vectores = actualizar_vectores(base)
```

```python
print("felino →", buscar("felino"))
print("perro →", buscar("perro"))
print("auto →", buscar("auto"))
```

### Introducción a problemas reales

Agregar ambigüedad:

```python
base.append("banco financiero")
base.append("banco de parque")

vectores = [embedding_frase(t) for t in base]

print(buscar("banco"))
print(buscar("banco financiero"))
print(buscar("banco parque"))
```

Resultado esperado:

inconsistente

