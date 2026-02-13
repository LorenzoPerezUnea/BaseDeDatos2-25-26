# Selección de Bases de Datos por Escenario

## Ejercicio 1: Gestión universitaria
**Base de datos recomendada:** Relacional (SQL)

El sistema maneja entidades con relaciones claras como estudiantes, materias y actas.  
Es imprescindible mantener consistencia estricta en las calificaciones y garantizar transacciones seguras.  
Las bases de datos SQL permiten cumplir con el modelo ACID y son adecuadas para esquemas estables sin requerimientos de escalado masivo.


## Ejercicio 2: Aplicación móvil
**Base de datos recomendada:** Clave–Valor (NoSQL)

La información almacenada es simple y se accede directamente mediante una clave.  
No existen relaciones entre los datos y se prioriza la velocidad de acceso.  
Además, los datos son temporales y pueden eliminarse automáticamente tras un periodo de inactividad.


## Ejercicio 3: Sensores industriales
**Base de datos recomendada:** Columnar (NoSQL)

Se gestionan grandes volúmenes de datos que crecen continuamente.  
Las consultas se enfocan en agregaciones y análisis históricos más que en registros individuales.  
Las bases columnar están optimizadas para lecturas analíticas y escalabilidad horizontal.


## Ejercicio 4: Sistema de contenidos
**Base de datos recomendada:** Documental (NoSQL)

Los artículos presentan estructuras variables según su tipo y el esquema cambia con frecuencia.  
El modelo documental permite almacenar información flexible y autocontenida.  
Esto evita migraciones constantes y facilita consultas dinámicas por distintos campos.


## Ejercicio 5: Sistema bancario
**Base de datos recomendada:** Relacional (SQL)

Las operaciones financieras requieren máxima fiabilidad y consistencia.  
Cada transacción debe ser atómica y duradera, incluso ante fallos del sistema.  
Las bases de datos relacionales garantizan estas propiedades críticas.


## Ejercicio 6: Red social
**Base de datos recomendada:** Grafos (NoSQL)

El análisis se centra en las relaciones entre usuarios, mensajes y dispositivos.  
Es necesario explorar conexiones indirectas y patrones complejos.  
Las bases de datos de grafos permiten recorridos eficientes que en SQL resultarían costosos.


## Ejercicio 7: Buscador semántico
**Base de datos recomendada:** Vectorial (NoSQL)

La búsqueda se basa en similitud de significado, no en coincidencias exactas.  
Se utilizan representaciones vectoriales para comparar documentos.  
Este enfoque es ideal para integraciones con modelos de lenguaje y embeddings.


## Ejercicio 8: Sistema corporativo
**Base de datos recomendada:** Relacional (SQL)

El modelo de datos es simple, con relaciones estables y volumen moderado.  
Las consultas son estructuradas y predecibles.  
No se justifica el uso de soluciones NoSQL en este escenario.