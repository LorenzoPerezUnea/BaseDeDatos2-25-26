# Ejercicios Avanzados

### Ejercicio 1

Medir rendimiento de consulta por nivel antes y después de crear índice.

### Ejercicio 2

Crear índice compuesto nivel + creditos y analizar orden de campos.

### Ejercicio 3

Ejecutar consulta solo por creditos y explicar por qué puede no usar índice compuesto.

### Ejercicio 4

Crear índice sobre cliente.ciudad en pedidos y ejecutar consulta con explain.

### Ejercicio 5

Crear índice único y probar inserción duplicada.

### Ejercicio 6

Crear índice parcial y analizar tamaño con getIndexes().

### Ejercicio 7

Identificar un campo de baja cardinalidad en cursos y debatir si conviene indexarlo.

### Ejercicio 8

Eliminar un índice con:

```js
db.cursos.dropIndex({ nivel: 1 })
```

Y volver a ejecutar explain.


