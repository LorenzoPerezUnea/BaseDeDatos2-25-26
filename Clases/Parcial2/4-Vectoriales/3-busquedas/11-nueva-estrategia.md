# Nueva estrategia de búsqueda

En lugar de buscar en toda la base, primero se selecciona una categoría probable.

```python
def seleccionar_categoria(query):
    if "gato" in query or "perro" in query or "felino" in query:
        return "animales"
    if "auto" in query or "coche" in query:
        return "vehiculos"
    if "rápido" in query or "lento" in query:
        return "velocidad"
    return "animales"
```

### Búsqueda sobre un subconjunto reducido

```python
def buscar_indexado(query):
    categoria = seleccionar_categoria(query)
    q_vec = embedding_frase_1(query)

    resultados = []

    for texto, vec in zip(indice[categoria], indice_vec[categoria]):
        sim = coseno(q_vec, vec)
        resultados.append((texto, sim))

    return sorted(resultados, key=lambda x: x[1], reverse=True)
```

### Ejecución comparativa con búsqueda lineal

```python
print(buscar_lineal("gato rápido")[:5])
print(buscar_indexado("gato rápido")[:5])
```

### Reducción del espacio de búsqueda

Se mide el número de comparaciones efectivas.

```python
def contar_comparaciones_indexado(query):
    categoria = seleccionar_categoria(query)
    return len(indice[categoria])

print(contar_comparaciones_indexado("gato rápido"))
```

### Comparación con el sistema completo

```python
print("Total base:", len(base))
print("Subconjunto indexado:", len(indice["animales"]))
```



