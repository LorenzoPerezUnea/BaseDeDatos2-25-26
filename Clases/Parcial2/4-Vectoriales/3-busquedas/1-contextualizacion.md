# Qué significaban realmente los ejercicios de la clase anterior

### El problema real que estamos resolviendo

En la clase anterior se construyeron embeddings manualmente, se cambiaron pesos, se añadieron dimensiones y se observaron cambios en la similitud.

Esos ejercicios no eran el objetivo final. Eran una forma de evidenciar algo más profundo:

un embedding es una forma de definir qué significa “parecido”o "similar".

No existe una única forma correcta de representar los datos. Cada decisión cambia el comportamiento del sistema.

### Qué significa cambiar un peso

Cuando se modifica algo como:

```python
vocabulario["gato"] = np.array([2, 0, 0, 0])
```

no se está “ajustando un número”.
Se está diciendo que ese concepto tiene más influencia en el espacio.

Esto tiene efectos directos:

* aumenta su impacto en combinaciones
* domina la similitud frente a otros términos
* altera el ranking de resultados

En términos prácticos:

cambiar pesos = cambiar la importancia de un concepto en las búsquedas

### Cuándo usar pesos mayores o menores

Los pesos se usan para priorizar información.

Ejemplos típicos:

* términos clave → pesos altos
* términos secundarios → pesos bajos
* ruido → pesos muy bajos o cercanos a cero

Si todo tiene el mismo peso:

el sistema no distingue qué es importante

Si un elemento tiene demasiado peso:

domina todas las comparaciones

### Qué significa usar valores negativos

Cuando se definía algo como:

```python
"lento": np.array([0, 0, 0, -1])
```

no es solo un número negativo.

Es una dirección opuesta en el espacio.

Esto permite modelar:

* conceptos contrarios
* tensiones semánticas (rápido vs lento)
* diferencias dentro de la misma categoría

Sin valores negativos:

todo se parece en la misma dirección

### Qué significa añadir una dimensión

Cuando se pasó de 3 a 4 dimensiones:

no se estaba “ampliando el vector”, se estaba añadiendo una nueva forma de describir los datos.

Cada dimensión es una pregunta implícita:

* ¿es un animal o no?
* ¿es un vehículo?
* ¿tiene velocidad?

Añadir dimensiones permite:

* capturar más información
* diferenciar mejor los elementos

Pero también tiene un coste:

* más complejidad
* más difícil de interpretar
* más difícil de ajustar manualmente

### Qué significa quitar o no usar dimensiones

Un espacio con pocas dimensiones:

* es más simple
* pero pierde capacidad de diferenciación

Ejemplo:

si solo existe “animal vs objeto”
entonces gato y perro son iguales

Quitar dimensiones simplifica, pero reduce precisión.

### Qué significa acercar o alejar conceptos

Cuando se modificaba:

```python
"perro": np.array([0.8, 0.2, 0, 0])
```

se estaba posicionando ese concepto más cerca de otro.

Esto define:

* qué se considera similar
* qué se considera distinto

En un sistema real:

esto afecta directamente a los resultados de búsqueda

### Qué problema estaban mostrando los ejercicios

Todos los experimentos apuntaban a lo mismo:

el comportamiento del sistema no depende de la búsqueda, depende del embedding

Si dos conceptos están mal representados:

* aparecerán mal ordenados
* se considerarán similares cuando no lo son
* o se separarán cuando deberían estar juntos

### Conexión con sistemas reales

En sistemas reales no se diseñan embeddings manualmente, pero el principio es el mismo:

* el modelo aprende estas posiciones
* el espacio vectorial se construye automáticamente
* pero sigue determinando todo el comportamiento

El modelo decide:

* qué palabras están cerca
* cuáles están lejos
* qué dimensiones existen implícitamente

### Por qué esto es importante antes de la búsqueda

Hasta ahora:

se comparaban todos los vectores entre sí

Eso funciona en ejemplos pequeños, pero no escala.

Si la base crece:

* miles de elementos
* millones de vectores

comparar todo con todo deja de ser viable


### Transición hacia la siguiente parte

Ya no se trata de cómo representar los datos, sino de cómo buscarlos.

El problema cambia:

antes:
cómo construir el espacio

ahora:
cómo encontrar rápidamente los vectores más cercanos

El embedding define el significado, pero la estructura de búsqueda define si el sistema es usable.

