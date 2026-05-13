# Construcción de la función de búsqueda

```python
def buscar(query, base, index, k=3):
    q = embedding(query).reshape(1, -1)
    dist, idx = index.search(q, k)

    resultados = []
    for j, i in enumerate(idx[0]):
        resultados.append((base[i], float(dist[0][j])))

    return resultados
```

### Qué hace realmente esta función

1. transforma la consulta en vector
2. proyecta la consulta en el mismo espacio
3. busca los puntos más cercanos
4. devuelve los textos asociados

### Propiedad fundamental

El sistema no busca coincidencias exactas.

Busca proximidad semántica.

### Ejecución inicial

```python
print(buscar("animal", base, index))
print(buscar("vehículo rápido", base, index))
print(buscar("felino", base, index))
```

### Qué observar

* resultados correctos sin coincidencia literal
* agrupación por significado
* comportamiento coherente del ranking
  

