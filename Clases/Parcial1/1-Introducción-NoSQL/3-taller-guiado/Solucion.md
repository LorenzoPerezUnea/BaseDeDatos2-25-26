Ejercicios – Selección de tipo de base de datos
Ejercicio 1 – Base de datos relacional (SQL)

Una base de datos relacional es adecuada para este sistema, ya que existen relaciones claras entre matrículas, asignaturas, profesores y actas de notas.
Es imprescindible mantener consistencia total en las calificaciones y asegurar que las operaciones se realicen de forma segura mediante transacciones.
El modelo de datos es estable y estructurado, por lo que no se requiere una solución más flexible o distribuida.

Ejercicio 2 – Base de datos Clave–Valor (NoSQL)

En este caso se prioriza el acceso rápido a la información mediante una clave única.
Los datos no están relacionados entre sí y tienen un carácter temporal, ya que pueden eliminarse tras un periodo de inactividad.
Una base de datos clave–valor permite simplicidad, velocidad y gestión eficiente de datos con caducidad.

Ejercicio 3 – Base de datos Columnar (NoSQL)

El sistema debe manejar un volumen muy elevado de datos generados continuamente por sensores industriales.
Las consultas se centran principalmente en análisis y agregaciones históricas, no en registros individuales.
Las bases de datos columnar están optimizadas para este tipo de cargas analíticas y permiten escalar fácilmente.

Ejercicio 4 – Base de datos Documental (NoSQL)

Cada artículo puede tener una estructura distinta según su tipo de contenido, y el modelo cambia con frecuencia.
Las bases de datos documentales permiten almacenar información sin un esquema rígido, adaptándose a campos variables.
Esto facilita la evolución del sistema sin necesidad de migraciones constantes.

Ejercicio 5 – Base de datos relacional (SQL)

Las transferencias bancarias requieren un nivel máximo de fiabilidad y consistencia.
Cada operación debe ejecutarse de forma atómica, evitando cualquier pérdida o duplicación de dinero.
Las bases de datos relacionales garantizan estas propiedades mediante transacciones ACID.

Ejercicio 6 – Base de datos de Grafos (NoSQL)

El objetivo principal es analizar relaciones entre usuarios, mensajes y dispositivos.
Se necesitan consultas que permitan recorrer conexiones directas e indirectas para detectar comunidades o patrones sospechosos.
Una base de datos de grafos está diseñada específicamente para este tipo de análisis relacional complejo.

Ejercicio 7 – Base de datos Vectorial (NoSQL)

El buscador debe encontrar documentos similares aunque no coincidan exactamente las palabras utilizadas.
Las bases de datos vectoriales permiten realizar búsquedas por similitud semántica mediante representaciones numéricas.
Este enfoque es ideal para sistemas basados en lenguaje natural.

Ejercicio 8 – Base de datos relacional (SQL)

El sistema maneja un volumen de datos moderado con relaciones bien definidas y estables.
Las consultas son estructuradas y previsibles, por lo que un modelo relacional resulta suficiente.
No se justifica el uso de una solución NoSQL más compleja.