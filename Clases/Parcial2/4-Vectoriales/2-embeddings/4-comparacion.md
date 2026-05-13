# Comparación entre espacios

```python
print("Espacio 1:")
print(coseno(embedding_frase_1("gato"), embedding_frase_1("perro")))

print("Espacio 2:")
print(coseno(embedding_frase_2("gato"), embedding_frase_2("perro")))
```

El mismo par de palabras produce resultados distintos dependiendo del diseño.

### Introducción de combinaciones

```python
print(embedding_frase_1("gato auto"))
print(embedding_frase_2("gato auto"))
```

En ambos casos se combinan dimensiones, pero el significado cambia según el espacio.

### Comparación cruzada

```python
print(coseno(embedding_frase_1("gato auto"), embedding_frase_1("auto")))
print(coseno(embedding_frase_2("gato auto"), embedding_frase_2("auto")))
```

El grado de similitud depende de cómo se distribuye la información en el vector.

### Modificación del diseño

Se modifica el primer espacio para acercar perro a gato.

```python
vocabulario_1["perro"] = np.array([0.8, 0.2, 0])
```

Reevaluar:

```python
print(embedding_frase_1("perro"))
print(coseno(embedding_frase_1("gato"), embedding_frase_1("perro")))
```

Ahora perro se acerca parcialmente a gato.

### Exploración sistemática

```python
palabras = ["gato", "felino", "perro", "auto"]

for p1 in palabras:
    for p2 in palabras:
        print(p1, p2, coseno(embedding_frase_1(p1), embedding_frase_1(p2)))
```

Este bloque permite observar todas las relaciones dentro del espacio.

