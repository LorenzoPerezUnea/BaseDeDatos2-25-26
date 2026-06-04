# Nueva dimensión

Se amplía el espacio para capturar otra característica.

```python
vocabulario_1 = {
    "gato": np.array([1, 0, 0, 0]),
    "felino": np.array([1, 0, 0, 0]),
    "perro": np.array([0.8, 0.2, 0, 0]),
    "auto": np.array([0, 0, 1, 0]),
    "rápido": np.array([0, 0, 0, 1]),
    "lento": np.array([0, 0, 0, -1])
}
```

### Evaluación con nueva dimensión

```python
def embedding_frase_1(texto):
    vector = np.zeros(4)
    for palabra in texto.lower().split():
        vector += vocabulario_1.get(palabra, np.zeros(4))
    return vector
```

```python
print(embedding_frase_1("gato rápido"))
print(embedding_frase_1("auto lento"))
```

Ahora el espacio incorpora información adicional sin cambiar las dimensiones anteriores.

### Comparación con nueva información

```python
print(coseno(embedding_frase_1("gato rápido"), embedding_frase_1("gato lento")))
print(coseno(embedding_frase_1("auto rápido"), embedding_frase_1("auto lento")))
```

La nueva dimensión introduce diferencias dentro del mismo tipo de entidad.

### Evaluación extendida

```python
print(coseno(embedding_frase_1("gato rápido"), embedding_frase_1("auto rápido")))
print(coseno(embedding_frase_1("gato"), embedding_frase_1("gato rápido")))
```

El comportamiento del sistema depende completamente de cómo se define el espacio vectorial.

