# Inestabilidad y fallos del espacio vectorial

### Sensibilidad del sistema a cambios en el embedding

Un espacio vectorial no es estable por defecto. Pequeñas modificaciones en los vectores pueden cambiar de forma significativa los resultados de similitud.

Se parte del vocabulario construido anteriormente.

```python
print(embedding_frase_1("gato"))
print(embedding_frase_1("perro"))
print(embedding_frase_1("auto"))
```

### Comparación base

```python
print(coseno(embedding_frase_1("gato"), embedding_frase_1("perro")))
print(coseno(embedding_frase_1("gato"), embedding_frase_1("auto")))
print(coseno(embedding_frase_1("perro"), embedding_frase_1("auto")))
```

Esto establece una referencia antes de introducir cambios.

### Aumento extremo de peso

Modificar un concepto para que domine el espacio.

```python
vocabulario_1["gato"] = np.array([10, 0, 0, 0])
```

Evaluar:

```python
print(embedding_frase_1("gato"))
print(coseno(embedding_frase_1("gato"), embedding_frase_1("felino")))
print(coseno(embedding_frase_1("gato"), embedding_frase_1("perro")))
```

El aumento de magnitud altera la relación con otros vectores.

### Evaluación en frases

```python
print(embedding_frase_1("gato rápido"))
print(coseno(embedding_frase_1("gato rápido"), embedding_frase_1("felino rápido")))
print(coseno(embedding_frase_1("gato rápido"), embedding_frase_1("perro rápido")))
```

Los efectos del cambio se propagan a todas las combinaciones.


