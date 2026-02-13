# 📊 Resolución de Casos de Arquitectura de Datos

Este repositorio contiene el análisis y la selección de motores de base de datos para 8 escenarios de negocio distintos, priorizando consistencia, rendimiento y escalabilidad.

---

## 🛠️ Solución de Ejercicios

### Ejercicio 1: Gestión Universitaria
* **Base de Datos:** Relacional (SQL) - *Ej: PostgreSQL / MariaDB*
* **Justificación:** Se requiere **consistencia fuerte** y transacciones **ACID**. En procesos de matrícula y actas, no puede haber estados intermedios ni pérdida de integridad.

### Ejercicio 2: Sesiones en App Móvil
* **Base de Datos:** Clave-Valor (NoSQL) - *Ej: Redis*
* **Justificación:** El acceso debe ser de baja latencia (milisegundos). Permite el uso de **TTL (Time To Live)** para que los tokens de sesión expiren automáticamente.

### Ejercicio 3: Sensores Industriales (IoT)
* **Base de Datos:** Series Temporales (Time-Series) - *Ej: InfluxDB / TimescaleDB*
* **Justificación:** Optimizado para la ingesta masiva de datos con marca de tiempo y consultas de agregación (promedios por día/planta) a gran escala.

### Ejercicio 4: CMS con Esquema Variable
* **Base de Datos:** Documental (NoSQL) - *Ej: MongoDB*
* **Justificación:** Ideal para contenido polimórfico. Permite que cada artículo tenga una estructura distinta (video, texto, galería) sin depender de un esquema rígido.



### Ejercicio 5: Transferencias Bancarias
* **Base de Datos:** Relacional (SQL) con alto nivel de aislamiento.
* **Justificación:** El cumplimiento estricto de **ACID** es vital. La atomicidad garantiza que si una parte de la transferencia falla, el dinero no "desaparezca".

### Ejercicio 6: Red Social y Conexiones
* **Base de Datos:** Orientada a Grafos - *Ej: Neo4j*
* **Justificación:** Facilita el recorrido de relaciones complejas (amigos de amigos, dispositivos compartidos) que en SQL requerirían "JOINS" excesivamente lentos.

### Ejercicio 7: Buscador Semántico
* **Base de Datos:** Vectorial o Motor de Búsqueda - *Ej: Pinecone / Elasticsearch*
* **Justificación:** Permite realizar **búsqueda semántica** (por significado) mediante embeddings, encontrando documentos similares aunque no compartan las mismas palabras exactas.

### Ejercicio 8: Sistema Corporativo Simple
* **Base de Datos:** Relacional (SQL) - *Ej: MySQL / SQLite*
* **Justificación:** Para datos moderados con relaciones bien definidas y estables (empleados/departamentos), una base de datos relacional estándar es la solución más eficiente y probada.

---

## 💻 Implementación en Java
Para conectar estos motores en un entorno Java, se recomienda:
* **JPA / Hibernate:** Para los casos SQL (1, 5, 8).
* **Spring Data Redis:** Para el caso 2.
* **Spring Data MongoDB:** Para el caso 4.
* **Neo4j Java Driver:** Para el caso 6.

