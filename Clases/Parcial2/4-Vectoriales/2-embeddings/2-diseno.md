# Primer diseño del espacio vectorial

Se define un espacio donde cada dimensión representa un tipo de entidad.

```python
vocabulario_1 = {
    "gato": np.array([1, 0, 0]),
    "felino": np.array([1, 0, 0]),
    "perro": np.array([0, 1, 0]),
    "auto": np.array([0, 0, 1])
}
```

En este diseño:

* dimensión 0 → gatos/felinos
* dimensión 1 → perros
* dimensión 2 → vehículos

### Función de embedding

```python
def embedding_frase_1(texto):
    vector = np.zeros(3)
    for palabra in texto.lower().split():
        vector += vocabulario_1.get(palabra, np.zeros(3))
    return vector
```

### Evaluación del primer espacio

```python
print(embedding_frase_1("gato"))
print(embedding_frase_1("felino"))
print(embedding_frase_1("perro"))
print(embedding_frase_1("auto"))
```

Se observa que cada palabra cae en una dimensión distinta, excepto los sinónimos.

### Comparación básica

```python
def coseno(a, b):
    if np.linalg.norm(a) == 0 or np.linalg.norm(b) == 0:
        return 0
    return np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b))
```

```python
print(coseno(embedding_frase_1("gato"), embedding_frase_1("felino")))
print(coseno(embedding_frase_1("gato"), embedding_frase_1("perro")))
```

En este diseño, los conceptos están completamente separados.


