# Inserción dinámica de datos

```python
sistema.agregar("avión de transporte internacional")

print(sistema.buscar("avión"))
```

### Qué ocurre internamente

* se añade un nuevo texto
* se recalculan embeddings
* se reconstruye el índice

### Justificación

Aunque no es eficiente para grandes volúmenes, este enfoque es:

* simple
* claro
* suficiente para aprendizaje

### Construcción de una interfaz básica

```python
def interfaz(sistema):
    while True:
        q = input("Consulta: ")

        if q == "salir":
            break

        resultados = sistema.buscar(q)

        print("\nResultados:")
        for r in resultados:
            print(r)
```

### Ejecución

```python
interfaz(sistema)
```

### Qué se consigue

Se transforma el sistema en:

* una herramienta interactiva
* un simulador de buscador real
* una base para el taller

### Control de parámetros

Modificar el comportamiento del sistema:

```python
print(sistema.buscar("animal", k=5))
print(sistema.buscar("vehículo", k=2))
```

### Qué se observa

* mayor k → más resultados, menor precisión
* menor k → menos resultados, mayor precisión

### Concepto importante

El sistema tiene parámetros que afectan directamente su comportamiento.



