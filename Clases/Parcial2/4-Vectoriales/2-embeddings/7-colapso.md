# Colapso del espacio vectorial

Forzar dos conceptos a ser iguales.

```python
vocabulario_1["perro"] = np.array([10, 0, 0, 0])
```

Evaluar:

```python
print(embedding_frase_1("gato"))
print(embedding_frase_1("perro"))
print(coseno(embedding_frase_1("gato"), embedding_frase_1("perro")))
```

Ambos conceptos ahora ocupan la misma posición.

### Impacto global

```python
print(coseno(embedding_frase_1("gato rápido"), embedding_frase_1("perro rápido")))
print(coseno(embedding_frase_1("gato lento"), embedding_frase_1("perro lento")))

print(coseno(embedding_frase_1("gato lento"), embedding_frase_1("perro rápido")))
print(coseno(embedding_frase_1("gato rápido"), embedding_frase_1("perro lento")))
```

La pérdida de diferenciación afecta a todo el sistema.

### Restauración parcial

```python
vocabulario_1["perro"] = np.array([0.8, 0.2, 0, 0])
```

```python
print(coseno(embedding_frase_1("gato"), embedding_frase_1("perro")))
```

Se recupera cierta separación entre conceptos.

