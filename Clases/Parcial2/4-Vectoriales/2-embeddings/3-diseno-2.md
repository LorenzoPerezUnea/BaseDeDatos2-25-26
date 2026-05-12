# Segundo diseño del espacio vectorial

Ahora se redefine el espacio con una lógica distinta. En lugar de separar por tipo exacto, se agrupan conceptos más cercanos.

```python
vocabulario_2 = {
    "gato": np.array([1, 0]),
    "felino": np.array([1, 0]),
    "perro": np.array([1, 0]),
    "auto": np.array([0, 1])
}
```

En este caso:

* dimensión 0 → animales
* dimensión 1 → objetos

### Nueva función de embedding

```python
def embedding_frase_2(texto):
    vector = np.zeros(2)
    for palabra in texto.lower().split():
        vector += vocabulario_2.get(palabra, np.zeros(2))
    return vector
```

### Evaluación del segundo espacio

```python
print(embedding_frase_2("gato"))
print(embedding_frase_2("perro"))
print(embedding_frase_2("auto"))
```

Ahora gato y perro tienen la misma representación.

