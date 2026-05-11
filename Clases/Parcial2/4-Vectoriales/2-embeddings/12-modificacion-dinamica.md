# Modificación dinámica de la base

Se agregan nuevas frases con combinaciones más complejas.

```python
base.append("gato salvaje rápido")
base.append("perro pequeño lento")
base.append("auto deportivo rápido")

vectores = [embedding_frase_1(t) for t in base]
```

### Evaluación tras expansión

```python
evaluar_query("gato")
evaluar_query("perro")
evaluar_query("rápido")
```

Los resultados cambian al introducir nuevos elementos.

### Evaluación comparativa

```python
evaluar_query("gato rápido")
evaluar_query("auto rápido")
```

Se observa cómo compiten múltiples resultados similares.


