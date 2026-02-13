# Respuestas y justificación – Tipos de bases de datos

## Ejercicio 1 – Base de datos relacional (SQL)

* Las entidades del sistema están claramente relacionadas entre sí
* Es imprescindible garantizar coherencia total en los datos
* Las operaciones deben ejecutarse mediante transacciones confiables (ACID)
* La estructura de la información es fija y bien definida
* No se requiere una escalabilidad masiva en múltiples nodos

## Ejercicio 2 – Base de datos Clave–Valor (NoSQL)

* La información se accede directamente a través de una clave única
* No existen dependencias ni relaciones entre los elementos almacenados
* Se busca máxima rapidez en las operaciones
* Los datos tienen carácter temporal y pueden caducar automáticamente
* No es necesario realizar consultas complejas

## Ejercicio 3 – Base de datos Columnar (NoSQL)

* Se manejan cantidades muy grandes de información en constante crecimiento
* Las consultas se enfocan en análisis agregados y métricas
* El sistema prioriza lecturas analíticas sobre escrituras puntuales
* Se analizan tendencias generales más que datos individuales
* Es fundamental que el sistema pueda escalar horizontalmente

## Ejercicio 4 – Base de datos Documental (NoSQL)

* Cada registro puede tener una estructura diferente
* El esquema de datos cambia con frecuencia
* Los datos se almacenan como unidades completas e independientes
* Permite búsquedas flexibles sobre distintos atributos
* Reduce la necesidad de modificar esquemas constantemente

## Ejercicio 5 – Base de datos relacional (SQL)

* El sistema opera en un entorno altamente sensible a errores
* La integridad de los datos es crítica
* Cada transacción debe ejecutarse de forma atómica y persistente
* Las relaciones entre cuentas y movimientos están bien definidas
* No se puede aceptar ningún tipo de inconsistencia en los datos

## Ejercicio 6 – Base de datos de Grafos (NoSQL)

* El principal interés está en cómo se conectan los datos
* Se analizan relaciones directas e indirectas entre entidades
* Las consultas implican recorridos entre nodos
* Las relaciones contienen información relevante por sí mismas
* Usar SQL implicaría consultas muy complejas y poco eficientes

## Ejercicio 7 – Base de datos Vectorial (NoSQL)

* El sistema necesita encontrar similitudes de significado
* No se basa en coincidencias exactas de texto
* Utiliza representaciones matemáticas en forma de vectores
* Se apoya en modelos de lenguaje o embeddings
* No es eficiente resolver este problema con bases de datos relacionales

## Ejercicio 8 – Base de datos relacional (SQL)

* La estructura de los datos es clara y sencilla
* El volumen de información es manejable
* Las relaciones entre entidades son estables
* Las consultas están bien definidas y son predecibles
* No es necesario incorporar soluciones NoSQL más complejas
