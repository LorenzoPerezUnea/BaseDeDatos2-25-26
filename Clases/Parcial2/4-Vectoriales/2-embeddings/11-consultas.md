# Consultas

Se define una función para evaluar una frase frente a toda la base.

```python
def evaluar_query(query):
    q_vec = embedding_frase_1(query)
    
    for texto, vec in zip(base, vectores):
        print(query, "vs", texto, "→", coseno(q_vec, vec))
```

### Evaluación de consultas simples

```python
evaluar_query("gato")
evaluar_query("auto")
evaluar_query("banco")
```

Se observa cómo el sistema posiciona la query respecto a todos los elementos.

### Evaluación de consultas compuestas

```python
evaluar_query("gato rápido")
evaluar_query("auto lento")
evaluar_query("banco financiero")
```

Las combinaciones generan resultados más específicos.

### Evaluación de términos ambiguos

```python
evaluar_query("banco")
```

El término se posiciona cerca de múltiples significados.

### Evaluación de términos fuera de contexto

```python
evaluar_query("animal")
```

El sistema genera resultados poco informativos debido a la falta de representación.

