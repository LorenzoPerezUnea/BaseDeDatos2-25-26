# Dirección vs tamaño

Aquí introducimos una idea fundamental:

* la dirección del vector representa el significado
* el tamaño puede ser irrelevante

Necesitamos una medida que ignore la magnitud.

# Similitud del coseno

Vamos a implementar una nueva función.

```python
def coseno(a, b):
    return np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b))
```

# Ejercicio guiado: probar coseno

```python
print("v1-v2:", coseno(v1, v2))
print("v1-v3:", coseno(v1, v3))
```

Resultado esperado:

* ambos cercanos a 1

Interpretación:
son prácticamente el mismo vector en dirección

# Comparación directa: distancia vs coseno

```python
def comparar(a, b):
    return {
        "distancia": np.linalg.norm(a - b),
        "coseno": coseno(a, b)
    }

print("v1-v2:", comparar(v1, v2))
print("v1-v3:", comparar(v1, v3))
```

Importante:

* distancia cambia mucho
* coseno se mantiene estable

Esto es exactamente lo que necesitamos en lenguaje natural.


