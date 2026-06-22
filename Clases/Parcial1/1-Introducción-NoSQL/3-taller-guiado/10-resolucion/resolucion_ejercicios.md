```md
# Respuestas y justificación

### Ejercicio 1 – Base de datos relacional (SQL)

* Las entidades mantienen relaciones claramente definidas  
* Es indispensable mantener consistencia fuerte en todo momento  
* Las operaciones deben respetar las propiedades ACID  
* El esquema de datos es fijo y bien estructurado  
* No se requiere una escalabilidad horizontal extrema  

### Ejercicio 2 – Base de datos Clave–Valor (NoSQL)

* Acceso rápido mediante una clave única  
* No se manejan relaciones entre registros  
* Se prioriza el rendimiento por sobre la complejidad de consultas  
* Los datos suelen ser temporales y con expiración  
* No se necesitan consultas avanzadas  

### Ejercicio 3 – Base de datos Columnar (NoSQL)

* Manejo de grandes volúmenes de información  
* Consultas enfocadas en agregaciones y análisis estadístico  
* Predominan las lecturas analíticas  
* El interés está en tendencias generales más que en filas individuales  
* Requiere capacidad de escalar horizontalmente  

### Ejercicio 4 – Base de datos Documental (NoSQL)

* Estructura de datos flexible entre documentos  
* El modelo puede cambiar con frecuencia  
* Cada documento contiene toda la información relevante  
* Permite consultas dinámicas sobre distintos campos  
* Reduce la necesidad de migraciones de esquema  

### Ejercicio 5 – Base de datos relacional (SQL)

* Entorno fuertemente orientado a transacciones  
* Las inconsistencias representan un riesgo elevado  
* Se requiere garantizar atomicidad y durabilidad  
* Relación bien definida entre cuentas y operaciones  
* La consistencia eventual no es aceptable  

### Ejercicio 6 – Base de datos de Grafos (NoSQL)

* La información principal reside en las relaciones  
* Se estudian vínculos directos e indirectos  
* Consultas basadas en recorridos entre nodos  
* Las relaciones tienen un significado propio  
* En SQL implicaría múltiples joins complejos  

### Ejercicio 7 – Base de datos Vectorial (NoSQL)

* Búsquedas basadas en similitud de significado  
* Comparaciones aproximadas en lugar de exactas  
* Uso de vectores como representación de datos  
* Integración con modelos de lenguaje y embeddings  
* Difícil de implementar eficientemente con SQL tradicional  

### Ejercicio 8 – Base de datos relacional (SQL)

* Esquema sencillo y claramente definido  
* Cantidad de datos manejable  
* Relaciones estables entre entidades  
* Consultas estructuradas y predecibles  
* No es necesario asumir la complejidad de NoSQL  
```
