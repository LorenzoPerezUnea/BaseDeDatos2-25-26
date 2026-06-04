# Ambigüedad

```python
base.extend([
    "banco financiero internacional",
    "banco de madera parque"
])

index, vectores = construir_indice(base)
```

### Ejecución

```python
print(buscar_con_score("banco", base, index))
```

### Qué observar

* mezcla de resultados
* scores similares
* falta de separación clara

### Justificación

El sistema no tiene:

* contexto
* desambiguación explícita
* conocimiento del dominio

Solo trabaja con proximidad semántica promedio.

### Desambiguación por contexto

```python
print(buscar_con_score("banco dinero", base, index))
print(buscar_con_score("banco sentarse", base, index))
```

### Qué cambia

* el embedding de la consulta se desplaza
* los resultados se separan
* el sistema mejora sin cambiar código

### Interpretación

El control del sistema no siempre se hace modificando código.

Muchas veces se hace modificando la entrada.

### Sensibilidad del sistema

Probar pequeñas variaciones:

```python
print(buscar_con_score("felino", base, index))
print(buscar_con_score("felino rápido", base, index))
print(buscar_con_score("felino salvaje rápido", base, index))
```

### Qué analizar

* cómo cambia el ranking
* cómo se reorganizan los resultados
* cómo influye cada palabra

### Concepto clave

El sistema es altamente sensible a la formulación de la consulta.

Esto es una propiedad estructural de los modelos de embeddings.

### Resultado

El sistema ahora:

* produce resultados interpretables
* permite ordenamiento explícito
* permite filtrado por relevancia
* muestra limitaciones reales
* responde a variaciones en la entrada

### Preparación para la siguiente parte

Con este sistema ya se dispone de:

* control básico del comportamiento
* capacidad de ajuste
* estructura modular

Esto permite encapsularlo y convertirlo en una herramienta reutilizable completa en la siguiente fase.

