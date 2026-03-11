# Plan Cache y selección automática de índices

MongoDB mantiene un cache de planes de ejecución.

La primera vez que ejecuta una consulta:

* Evalúa posibles planes
* Mide rendimiento inicial
* Guarda el plan ganador

Las siguientes ejecuciones:

* Usan el plan cacheado

Esto mejora rendimiento, pero también puede generar problemas si:

* Cambia la distribución de datos
* El índice óptimo deja de ser óptimo

### Experimento didáctico

1. Crear dos índices posibles.
2. Ejecutar consulta.
3. Observar winningPlan.
4. Eliminar uno.
5. Volver a ejecutar.

Este ejercicio muestra cómo MongoDB toma decisiones.

### Concepto clave

MongoDB no siempre usa el índice “más obvio”.
Usa el que estima como menos costoso.

Y esa estimación depende de estadísticas internas.


