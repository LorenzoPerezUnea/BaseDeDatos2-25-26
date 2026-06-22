
# Respuestas y justificación

### Ejercicio 1 – Base de datos relacional (SQL)

* Las entidades mantienen relaciones claramente establecidas  
* Es imprescindible garantizar consistencia estricta en todo momento  
* Las operaciones deben respetar las propiedades ACID  
* El esquema de datos es fijo y bien estructurado  
* No se requiere un escalado horizontal intensivo  

### Ejercicio 2 – Base de datos Clave–Valor (NoSQL)

* Acceso rápido mediante una clave única  
* No se manejan relaciones entre los elementos almacenados  
* Se prioriza el rendimiento frente a la complejidad  
* La información es temporal y puede caducar automáticamente  
* No se necesitan consultas avanzadas  

### Ejercicio 3 – Base de datos Columnar (NoSQL)

* Manejo de grandes volúmenes de información  
* Consultas enfocadas en agregaciones y análisis estadístico  
* Predominan las lecturas analíticas sobre las transaccionales  
* El interés está en tendencias globales más que en datos individuales  
* Es necesario escalar horizontalmente  

### Ejercicio 4 – Base de datos Documental (NoSQL)

* Las entidades no comparten una estructura fija  
* El esquema cambia con frecuencia  
* Cada documento es independiente y autosuficiente  
* Se requieren consultas flexibles sobre distintos campos  
* Se evita la necesidad de modificar esquemas constantemente  

### Ejercicio 5 – Base de datos relacional (SQL)

* Entorno altamente transaccional  
* Las inconsistencias suponen un riesgo crítico  
* Se exige atomicidad y persistencia de los datos  
* Relación clara entre cuentas y operaciones  
* La consistencia eventual no es aceptable  

### Ejercicio 6 – Base de datos de Grafos (NoSQL)

* La información clave reside en las relaciones  
* Se analizan conexiones directas e indirectas  
* Las consultas se basan en recorridos y vínculos  
* Las relaciones poseen significado propio  
* En SQL implicaría múltiples joins complejos  

### Ejercicio 7 – Base de datos Vectorial (NoSQL)

* Búsquedas basadas en similitud de significado  
* Comparaciones aproximadas en lugar de exactas  
* Uso de vectores como representación de datos  
* Integración con embeddings o modelos de lenguaje  
* SQL tradicional no resulta eficiente  

### Ejercicio 8 – Base de datos relacional (SQL)

* Esquema sencillo y claramente definido  
* Cantidad de datos manejable  
* Relaciones estables entre entidades  
* Consultas estructuradas y predecibles  
* No compensa adoptar soluciones NoSQL  
