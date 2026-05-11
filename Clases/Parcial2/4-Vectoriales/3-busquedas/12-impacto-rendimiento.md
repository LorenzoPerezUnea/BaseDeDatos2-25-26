# Impacto en rendimiento

```python
import time

start = time.time()
buscar_indexado("gato rápido")
end = time.time()

print("Tiempo indexado:", end - start)
```

### Comparación directa de escalabilidad

```python
start = time.time()
buscar_lineal("gato rápido")
end = time.time()

print("Lineal:", end - start)

start = time.time()
buscar_indexado("gato rápido")
end = time.time()

print("Indexado:", end - start)
```

### Limitación del índice manual

El sistema funciona, pero presenta problemas estructurales:

* la clasificación es rígida
* depende de reglas manuales
* no captura relaciones complejas

### Necesidad de índices automáticos

En sistemas reales, no se usan reglas manuales como:

```python
if "gato" in texto:
```

En su lugar, se usan estructuras que aprenden la organización del espacio vectorial.


