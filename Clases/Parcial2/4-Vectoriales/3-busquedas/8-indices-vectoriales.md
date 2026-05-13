# Índices vectoriales

En sistemas reales, esta idea se implementa mediante estructuras de indexación.

Una de las más utilizadas es FAISS:

Facebook AI Similarity Search

FAISS no cambia cómo se representan los vectores, sino cómo se organizan para ser buscados.

### Qué hace realmente un índice vectorial

Un índice vectorial tiene dos fases:

### Construcción del índice

Los vectores se agrupan o estructuran internamente.

Esto puede hacerse de distintas formas:

* partición del espacio
* agrupación por similitud
* construcción de grafos

### Búsqueda aproximada

Cuando llega una consulta:

* se identifica una zona relevante del espacio
* solo se comparan vectores dentro de esa zona
* se reduce drásticamente el número de comparaciones

### Comparación conceptual con búsqueda lineal

```text
Búsqueda lineal:
consulta → todos los vectores → ranking final

Búsqueda indexada:
consulta → región relevante → subset de vectores → ranking final```
```

### Idea clave: no se busca exactitud total desde el inicio

En sistemas vectoriales modernos:

* primero se reduce el problema
* luego se calcula la similitud exacta

Esto introduce una estrategia fundamental:

aproximar primero, calcular después

