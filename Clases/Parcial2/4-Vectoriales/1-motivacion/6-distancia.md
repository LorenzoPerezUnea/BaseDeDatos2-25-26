# Problema: no toda distancia significa lo mismo

En la parte anterior usamos distancia euclidiana.

Funcionaba bien para ejemplos simples, pero ahora vamos a tensionar el modelo.

Ejecutar:

```python
import numpy as np

a = np.array([1, 1])
b = np.array([2, 2])
c = np.array([10, 10])

def distancia(a, b):
    return np.linalg.norm(a - b)

print("a-b:", distancia(a, b))
print("a-c:", distancia(a, c))
```

Hasta aquí todo parece lógico:

* b está más cerca de a que c

Pero ahora viene el problema.

### Ejercicio guiado: mismo significado, distinta magnitud

```python
v1 = np.array([1, 1])
v2 = np.array([2, 2])
v3 = np.array([3, 3])

print("v1-v2:", distancia(v1, v2))
print("v1-v3:", distancia(v1, v3))
```

Interpretación:

* todos apuntan en la misma dirección
* deberían ser "igual de similares"
* pero la distancia dice que no

Esto rompe nuestra intuición semántica.


