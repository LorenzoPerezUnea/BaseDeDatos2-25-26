# Transición hacia FAISS

### Objetivo

Implementar una estructura de búsqueda más eficiente que la búsqueda lineal, introduciendo un índice vectorial simplificado que reduzca el número de comparaciones.

### Construcción de un índice por agrupación simple

En lugar de comparar contra todos los vectores, se construye una estructura de agrupación por categorías aproximadas.

La idea es simular cómo un índice reduce el espacio de búsqueda.

```python
indice = {
    "animales": [],
    "vehiculos": [],
    "velocidad": []
}
```

### Clasificación de vectores en el índice

Cada texto se asigna a una categoría aproximada según su contenido.

```python
def clasificar(texto):
    if "gato" in texto or "perro" in texto or "felino" in texto:
        return "animales"
    if "auto" in texto or "coche" in texto:
        return "vehiculos"
    if "rápido" in texto or "lento" in texto:
        return "velocidad"
    return "otros"
```

### Construcción del índice

Se distribuyen los elementos de la base en el índice.

```python
for texto in base:
    categoria = clasificar(texto)
    indice[categoria].append(texto)

print({k: len(v) for k, v in indice.items()})
```

### Embeddings del índice

Se generan embeddings por separado para cada grupo.

```python
indice_vec = {
    k: [embedding_frase_1(t) for t in v]
    for k, v in indice.items()
}
```

