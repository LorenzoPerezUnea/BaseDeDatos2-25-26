# Hacia estructuras de búsqueda vectorial

### Objetivo de esta parte

El cambio fundamental es pasar de:

búsqueda exhaustiva → búsqueda aproximada estructurada

### Idea clave: no todos los vectores deben compararse

En un espacio vectorial, no todos los puntos son candidatos relevantes para una consulta.

Si una consulta tiene un vector dirección específico:

* solo una región del espacio es relevante
* el resto puede descartarse sin cálculo exacto

Esto permite reducir drásticamente el número de comparaciones necesarias.

### Agrupación conceptual del espacio

En lugar de tratar la base como una lista plana, se puede imaginar como un espacio dividido en regiones.

Cada región contiene vectores “similares entre sí”.

```text
[ región A ] → animales
[ región B ] → vehículos
[ región C ] → conceptos de velocidad
```

Una consulta primero determina la región probable, y luego solo compara dentro de ella.

