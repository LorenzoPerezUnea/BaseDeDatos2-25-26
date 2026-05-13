# Construcción de una “base de datos” mínima

Vamos a construir algo más cercano a una BD.

```python
base = ["gato", "felino", "perro", "auto"]
```

### Ejercicio guiado: búsqueda por similitud

```python
base = ["gato", "felino", "perro", "auto"]

def buscar(query):
    q_vec = embedding_simple(query)
    resultados = []

    for item in base:
        vec = embedding_simple(item)
        d = distancia(q_vec, vec)
        resultados.append((item, d))

    return sorted(resultados, key=lambda x: x[1])

print(buscar("gato"))
```

# Análisis

¿Qué está pasando?

1. convertimos query → vector
2. comparamos con todos
3. calculamos distancia
4. ordenamos

Esto es exactamente lo que hará una base vectorial real.

# Experimentos

Probar diferentes queries:

```python
print(buscar("felino"))
print(buscar("perro"))
print(buscar("auto"))
```

Luego modificar el embedding:

```python
# cambiar felino para que esté más lejos
```

Y observar cómo cambian resultados.

### Conexión con lo que ya conocen

Comparar explícitamente:

SQL:

* WHERE nombre = valor

Grafos:

* MATCH exacto

Vectores:

* buscar por cercanía

Aquí no hay igualdad.
Hay proximidad.

