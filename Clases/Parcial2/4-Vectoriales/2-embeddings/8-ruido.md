# Ruido en el espacio

Modificar el comportamiento de palabras desconocidas.

```python
def embedding_palabra_ruido(p):
    if p in vocabulario_1:
        return vocabulario_1[p]
    return np.array([0.05, 0.05, 0.05, 0.05])
```

Nueva función de frase:

```python
def embedding_frase_ruido(texto):
    vector = np.zeros(4)
    for palabra in texto.lower().split():
        vector += embedding_palabra_ruido(palabra)
    return vector
```

### Evaluación con ruido

```python
print(embedding_frase_ruido("animal"))
print(coseno(embedding_frase_ruido("animal"), embedding_frase_ruido("gato")))
```

El ruido evita vectores vacíos pero introduce ambigüedad.

### Efecto acumulativo del ruido

```python
print(embedding_frase_ruido("animal rápido"))
print(embedding_frase_ruido("animal lento"))
print(coseno(embedding_frase_ruido("animal rápido"), embedding_frase_ruido("animal lento")))
```

El sistema empieza a generar similitudes poco informativas.

