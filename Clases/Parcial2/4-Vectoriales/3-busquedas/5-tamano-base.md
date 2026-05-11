# Aumento progresivo del tamaño de la base

```python
base = base * 2
vectores = [embedding_frase_1(t) for t in base]

print(len(base))
```

Aquí el sistema sigue siendo el mismo, pero:

* hay más datos
* hay más comparaciones
* el coste aumenta

### Nueva medición

```python
start = time.time()
buscar_lineal("gato rápido")
end = time.time()

print("Tiempo:", end - start)
```

Ahora el tiempo debería ser mayor.

Esto permite observar cómo crece el coste.

### Comparación entre diferentes tamaños

```python
sizes = [100, 1000, 5000]

for s in sizes:
    test_base = base[:s]
    test_vectores = vectores[:s]

    start = time.time()
    q_vec = embedding_frase_1("gato rápido")

    for vec in test_vectores:
        coseno(q_vec, vec)

    end = time.time()

    print("Tamaño:", s, "Tiempo:", end - start)
```

Aquí se elimina el ordenamiento y se mide solo el coste de comparar.

Esto permite separar:

* coste de comparación
* coste de ordenamiento

### Evaluación de múltiples queries

```python
queries = ["gato", "perro", "auto", "rápido", "lento"]

for q in queries:
    start = time.time()
    buscar_lineal(q)
    end = time.time()
    print(q, "→", end - start)
```

Se observa que:

* el tiempo depende del tamaño de la base
* no depende del contenido de la query

### Inspección de comportamiento repetitivo

```python
resultados = buscar_lineal("auto rápido")

for r in resultados[:10]:
    print(r)
```

Dado que hay duplicados:

* muchos resultados serán iguales
* el sistema no distingue instancias idénticas

### Ejecución intensiva

```python
for i in range(10):
    buscar_lineal("gato rápido")
```

Se simula un sistema con múltiples consultas.

### Medición acumulada

```python
start = time.time()

for i in range(20):
    buscar_lineal("gato rápido")

end = time.time()

print("Tiempo total:", end - start)
```

Esto aproxima el comportamiento bajo carga.


