# Ambigüedad controlada

```python
vocabulario_1["banco"] = np.array([0.5, 0.5, 0, 0])
```

Evaluar:

```python
print(embedding_frase_1("banco"))
```

### Uso en diferentes contextos

```python
print(embedding_frase_1("banco financiero"))
print(embedding_frase_1("banco parque"))
```

Ambas frases comparten una base común.

### Comparación directa

```python
print(coseno(embedding_frase_1("banco financiero"), embedding_frase_1("banco parque")))
```

La similitud es alta debido a la ambigüedad.

### Introducción de nuevas dimensiones de contexto

```python
vocabulario_1["financiero"] = np.array([0, 0, 1, 0])
vocabulario_1["parque"] = np.array([0, 0, 0, 1])
```

### Evaluación con contexto

```python
print(embedding_frase_1("banco financiero"))
print(embedding_frase_1("banco parque"))
```

### Comparación tras el ajuste

```python
print(coseno(embedding_frase_1("banco financiero"), embedding_frase_1("banco parque")))
```

El sistema comienza a separar los significados.

### Exploración de combinaciones complejas

```python
print(embedding_frase_1("banco financiero rápido"))
print(embedding_frase_1("banco parque lento"))
print(coseno(embedding_frase_1("banco financiero rápido"), embedding_frase_1("banco parque lento")))
```

La interacción entre dimensiones muestra cómo el significado depende de múltiples factores simultáneamente.

