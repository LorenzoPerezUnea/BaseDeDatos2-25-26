# Mejora del sistema: control del ranking y comportamiento

### Objetivo operativo

El sistema construido en la parte anterior ya funciona, pero todavía está en un estado técnico:

* devuelve distancias
* no es interpretable
* no permite control fino del comportamiento

El objetivo ahora es transformar ese sistema en algo utilizable, configurable y más cercano a un sistema real.

### Problema inicial

La función actual devuelve:

```text
("texto", distancia)
```

Esto presenta varios problemas:

* la distancia no es intuitiva
* no hay criterio claro de relevancia
* no se puede filtrar fácilmente
* no se puede comparar entre resultados

### Paso 1 – Transformación a score

```python
def buscar_con_score(query, base, index, k=3):
    q = embedding(query).reshape(1, -1)
    dist, idx = index.search(q, k)

    resultados = []
    for j, i in enumerate(idx[0]):
        distancia = float(dist[0][j])
        score = 1 / (1 + distancia)

        resultados.append({
            "texto": base[i],
            "distancia": distancia,
            "score": score
        })

    return resultados
```

### Justificación

Se introduce una función de transformación:

```text
score = 1 / (1 + distancia)
```

Esto permite:

* invertir la lógica (menor distancia → mayor score)
* acotar valores (entre 0 y 1)
* facilitar interpretación

### Ejecución inicial

```python
res = buscar_con_score("felino salvaje", base, index)

for r in res:
    print(r)
```

### Qué observar

* los resultados ahora tienen una medida interpretable
* los valores altos indican mayor relevancia
* el orden puede no estar garantizado aún
  

