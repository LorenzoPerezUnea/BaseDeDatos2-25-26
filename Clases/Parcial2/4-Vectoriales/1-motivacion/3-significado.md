# Conectando con significado

Ahora hacemos un salto conceptual importante:

vamos a usar vectores para representar significado

No es matemáticamente obvio, pero es la base de todo.

Ejemplo conceptual:

* "gato" → punto A
* "felino" → punto cercano a A
* "auto" → punto lejano

### Ejercicio guiado: simulación manual de significado

```python
gato = np.array([1.0, 1.0])
felino = np.array([1.1, 1.05])
perro = np.array([0.9, 1.0])
auto = np.array([-1.0, -1.0])

def distancia(a, b):
    return np.linalg.norm(a - b)

print("gato-felino:", distancia(gato, felino))
print("gato-perro:", distancia(gato, perro))
print("gato-auto:", distancia(gato, auto))
```

Aquí ocurre algo muy importante:

sin usar lenguaje natural real,
ya estamos modelando significado

