# Orden explícito de resultados

Aunque FAISS devuelve resultados ordenados por distancia, es importante hacer explícito el criterio.

```python
def ordenar_resultados(resultados):
    return sorted(resultados, key=lambda x: x["score"], reverse=True)
```

### Ejecución

```python
res = buscar_con_score("vehículo", base, index)
res = ordenar_resultados(res)

for r in res:
    print(r)
```

### Justificación

Separar:

* generación de resultados
* ordenamiento

permite:

* cambiar criterios en el futuro
* introducir reglas adicionales
* mantener el sistema modular

### Filtrado por relevancia

```python
def filtrar(resultados, umbral=0.5):
    return [r for r in resultados if r["score"] > umbral]
```

### Ejecución

```python
res = buscar_con_score("animal", base, index)
res = filtrar(res, 0.6)

for r in res:
    print(r)
```

### Qué se busca

* eliminar resultados poco relevantes
* controlar la calidad de salida
* simular comportamiento de sistemas reales

### Interpretación

En sistemas reales, rara vez se muestran todos los resultados.

Siempre hay:

* umbrales
* filtros
* reglas de corte
  

