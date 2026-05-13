# Observación del coste computacional

```python
n = len(base)
print("Número de comparaciones aproximadas:", n)
```

Cada búsqueda implica:

* una comparación por cada elemento
* crecimiento lineal

### Evaluación directa de similitudes

```python
q_vec = embedding_frase_1("gato rápido")

for i in range(5):
    print(coseno(q_vec, vectores[i]))
```

Se observa el cálculo básico sin ordenamiento.

### Comparación completa sin ordenar

```python
q_vec = embedding_frase_1("gato rápido")

similitudes = []

for vec in vectores:
    similitudes.append(coseno(q_vec, vec))

print(similitudes[:10])
```

Esto permite ver:

* todos los valores de similitud
* distribución de resultados

### Evaluación del coste de ordenamiento

```python
import random

simulacion = [(random.random(), i) for i in range(len(base))]

start = time.time()
sorted(simulacion, reverse=True)
end = time.time()

print("Tiempo ordenando:", end - start)
```

Aquí se observa que:

* no solo comparar cuesta tiempo
* ordenar también tiene impacto
* ambos costes crecen con el tamaño de los datos

### Resumen

El sistema de búsqueda lineal funciona porque compara cada vector con la consulta, pero ese diseño implica que:

* el coste crece proporcionalmente al tamaño de la base
* cada consulta repite el mismo trabajo desde cero
* no existe ninguna estructura que reduzca candidatos

Esto hace que el modelo sea correcto en resultados, pero ineficiente por diseño.

