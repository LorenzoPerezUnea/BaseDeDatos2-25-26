# Ejecución de una búsqueda simple

```python
resultados = buscar_lineal("gato rápido")
print(resultados[:5])
```

Aquí se observa:

* qué elementos aparecen arriba
* cómo el sistema ordena por similitud

### Inspección detallada de resultados

```python
for r in resultados[:10]:
    print(r)
```

Esto permite analizar:

* si los resultados tienen sentido
* si hay empates
* si aparecen resultados inesperados

### Medición de tiempo de ejecución

Se mide cuánto tarda una búsqueda.

```python
import time

start = time.time()
buscar_lineal("gato rápido")
end = time.time()

print("Tiempo:", end - start)
```

Este valor representa el coste de recorrer toda la base.

### Repetición de la medición

```python
for _ in range(5):
    start = time.time()
    buscar_lineal("gato rápido")
    end = time.time()
    print(end - start)
```

Se repite para:

* evitar mediciones puntuales
* observar variaciones
* obtener una referencia más estable
  

