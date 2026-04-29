# Primer concepto clave: vector

Un vector, en este contexto, es simplemente una lista de números.

Vamos a empezar con algo básico.

```python
import numpy as np

v = np.array([1, 2, 3])
print(v)
```

### Interpretación geométrica simple

Vamos a bajar a 2 dimensiones para entenderlo mejor.

```python
a = np.array([1, 1])
b = np.array([4, 5])

distancia = np.linalg.norm(a - b)
print("Distancia:", distancia)
```

### Ejercicio guiado 1: explorar distancias

Cambiar valores en vivo.

```python
p1 = np.array([0, 0])
p2 = np.array([1, 1])
p3 = np.array([10, 10])

print("p1-p2:", np.linalg.norm(p1 - p2))
print("p1-p3:", np.linalg.norm(p1 - p3))
```

Interpretación:

* p1 y p2 → cerca
* p1 y p3 → lejos

Introducir idea:
distancia = similitud inversa

nota:
La afirmación **"distancia = similitud inversa"** es un concepto fundamental en minería de datos, machine learning y análisis espacial, donde se establece una relación inversa entre la cercanía física o conceptual de dos objetos y su parecido.

