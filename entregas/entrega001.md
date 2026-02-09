# Resolución de Casos de Uso: Selección de Bases de Datos

Este documento detalla la elección tecnológica para cada ejercicio basándose en el análisis de factores de datos, volumen y relaciones.

---

### Ejercicio 1: Universidad (Matrículas y Notas)
* **Decisión:** **SQL (Relacional)**.
* **Justificación:** El sistema requiere **consistencia fuerte** en las calificaciones y transacciones seguras. Para datos estructurados donde la integridad es crítica, SQL es la opción adecuada frente a modelos NoSQL que priorizan la disponibilidad.

### Ejercicio 2: Aplicación Móvil (Sesiones y Preferencias)
* **Decisión:** **Clave–Valor**.
* **Justificación:** Se requiere un acceso inmediato (latencia mínima) para datos simples asociados a una clave. Además, este modelo soporta **TTL (Time To Live)**, permitiendo que los datos expiren automáticamente tras inactividad.

### Ejercicio 3: Sensores Industriales (Big Data Analítico)
* **Decisión:** **Columnar**.
* **Justificación:** El escenario implica un **volumen masivo** de datos homogéneos y la necesidad de realizar **agregaciones** (resúmenes por día o planta). Las bases columnares optimizan las lecturas analíticas y reducen el I/O al trabajar con columnas específicas.

### Ejercicio 4: Gestión de Contenidos (CMS Flexible)
* **Decisión:** **Documental**.
* **Justificación:** Se destaca la necesidad de manejar **estructuras variables** y un modelo que cambia con frecuencia. Las bases documentales permiten **esquemas dinámicos**, almacenando cada artículo como un documento autocontenido.

### Ejercicio 5: Banco (Transferencias Consistentes)
* **Decisión:** **SQL (Relacional)**.
* **Justificación:** La prioridad es la **consistencia fuerte** y la seguridad transaccional para evitar la pérdida de dinero. Este es un caso típico de datos estructurados con reglas de integridad estrictas.

### Ejercicio 6: Red Social (Detección de Fraude)
* **Decisión:** **Grafos**.
* **Justificación:** El foco es identificar **caminos indirectos** y relaciones complejas entre entidades. En este modelo, las relaciones son **"ciudadanos de primera clase"**, permitiendo analizar conexiones de segundo o tercer nivel de forma eficiente.

### Ejercicio 7: Buscador Semántico (Documentos Similares)
* **Decisión:** **Vectorial**.
* **Justificación:** Se requiere encontrar documentos por **similitud semántica** sin necesidad de coincidencia exacta de palabras. Estas bases están diseñadas para almacenar **embeddings numéricos** y realizar comparaciones matemáticas de proximidad.

### Ejercicio 8: Sistema Corporativo (Jerarquía Simple)
* **Decisión:** **SQL (Relacional)**.
* **Justificación:** Para un volumen moderado con relaciones **bien definidas y estables**, el modelo relacional es suficiente. No presenta la complejidad o variabilidad que justificaría el uso de arquitecturas NoSQL.