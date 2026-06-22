# Solución de Taller: Introducción a NoSQL
## 1. Gestión Académica (Matrículas y Notas)
**Enunciado:** Universidad necesita gestionar matrículas y notas. Requiere consistencia fuerte y transacciones seguras.

* **Solución:** **Base de Datos Relacional (SQL)**
* **Justificación:**
    * **ACID estricto:** No se pueden permitir errores en notas o matrículas duplicadas.
    * **Integridad referencial:** La relación entre Alumno, Asignatura y Nota es rígida y vital.
    * **Estabilidad:** El modelo de datos académico cambia muy poco con los años.

## 2. Aplicación Móvil (Sesiones y Preferencias)
**Enunciado:** App móvil con preferencias de usuario y tokens de sesión. Acceso inmediato y datos que se eliminan automáticamente.

* **Solución:** **NoSQL Clave-Valor**
* **Justificación:**
    * **Baja Latencia:** El acceso es por clave primaria (Token ID), lo que garantiza velocidad máxima (O(1)).
    * **TTL (Time-To-Live):** Estas BD permiten definir cuándo expira un dato automáticamente (perfecto para sesiones).
    * **Simplicidad:** No se requieren relaciones complejas (JOINs).

## 3. Sensores Industriales (Analytics / Big Data)
**Enunciado:** Millones de registros diarios de sensores. Consultas de resúmenes (agregaciones) por día/planta. Volumen en aumento.

* **Solución:** **NoSQL Columnar (Wide-Column)**
* **Justificación:**
    * **Escritura masiva:** Optimizadas para ingerir millones de datos por segundo.
    * **Consultas analíticas:** Al guardar datos por columnas, calcular el "promedio de temperatura" es mucho más rápido que en una base orientada a filas.
    * **Compresión:** Los datos repetitivos de sensores se comprimen muy bien en este formato.

## 4. Sistema de Gestión de Contenidos (CMS)
**Enunciado:** Artículos con campos distinto según su tipo (galerías, videos, texto). El modelo cambia con frecuencia.

* **Solución:** **NoSQL Documental**
* **Justificación:**
    * **Esquema Flexible (Schemaless):** Permite guardar JSONs con estructuras diferentes en la misma colección sin alterar la tabla.
    * **Iteración rápida:** Si mañana se añade un campo "TikTok", no hay que migrar toda la base de datos.
    * **Agregación natural:** El documento contiene toda la info del artículo, evitando JOINs.

## 5. Sistema Bancario (Core Bancario)
**Enunciado:** Registro de transferencias entre cuentas. Asegurar que nunca se pierda dinero. Consistencia total ante fallos.

* **Solución:** **Base de Datos Relacional (SQL)**
* **Justificación:**
    * **Transaccionalidad Crítica:** Requiere `COMMIT` y `ROLLBACK` robustos. Si falla el sistema a mitad de una transferencia, el dinero no debe desaparecer.
    * **Consistencia Inmediata:** No se acepta "consistencia eventual" en saldos bancarios.

## 6. Red Social (Detección de Fraude/Comunidades)
**Enunciado:** Detectar **comunidades**, relaciones indirectas y conexiones sospechosas entre perfiles.

* **Solución:** **NoSQL de Grafos**
* **Justificación:**
    * **Relaciones como prioridad:** En SQL, buscar "amigos de amigos" requiere JOINs recursivos costosos. En Grafos, es una travesía nativa y eficiente.
    * **Patrones complejos:** Ideal para detectar ciclos o caminos entre nodos distantes (análisis de fraude).

## 7. Buscador Semántico (IA)
**Enunciado:** Encontrar documentos **similares** a una descripción, aunque **no coincidan las palabras exactas**.

* **Solución:** **Base de Datos Vectorial**
* **Justificación:**
    * **Búsqueda por similitud:** Utiliza embeddings (vectores numéricos) para entender el contexto semántico.
    * **Distancia matemática:** Calcula la "cercanía" entre la consulta y los documentos, algo que SQL tradicional (LIKE) no puede hacer.

## 8. Gestión Corporativa Simple (RRHH)
**Enunciado:** Empleados y departamentos. Volumen*moderado, relaciones bien definidas y estables.

* **Solución:** **Base de Datos Relacional (SQL)**
* **Justificación:**
    * **Simplicidad y Madurez:** Para problemas estándar con datos estructurados y bajo volumen, SQL es la opción más mantenible y con mayor soporte.
    * **Normalización:** Los datos se adaptan perfectamente a tablas y claves foráneas.

