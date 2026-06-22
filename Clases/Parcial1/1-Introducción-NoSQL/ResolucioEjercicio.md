# Ejercicio 1

**Solución:** Base de datos Relacional (SQL)

**Justificación:**
* **Consistencia fuerte:** Se requiere asegurar la consistencia exacta en las calificaciones, lo cual garantizan las propiedades ACID (Atomicidad, Consistencia, Aislamiento, Durabilidad) de las bases relacionales.
* **Transacciones seguras:** En procesos críticos como las matrículas, es obligatorio el uso de transacciones fuertes para evitar errores, una característica donde NoSQL suele ser más débil o "eventual".
* **Entorno tradicional:** Los sistemas académicos y administrativos son ejemplos clásicos donde el modelo relacional funciona mejor debido a su estructura organizada y confiable.

---

# Ejercicio 2

**Solución:** Base de datos NoSQL Clave–Valor

**Justificación:**
* **Alta velocidad:** Se prioriza el acceso inmediato a la información, una de las principales ventajas del modelo clave-valor.
* **Gestión de sesiones:** Es el caso de uso por excelencia para almacenar tokens de sesión y configuraciones temporales de usuario.
* **Datos temporales:** Ideal para información que puede eliminarse automáticamente (caché o expiración) y que no requiere relaciones complejas.

---

# Ejercicio 3

**Solución:** Base de datos NoSQL Columnar

**Justificación:**
* **Escala masiva (Big Data):** Diseñada para manejar millones de registros y volúmenes de datos que crecen constantemente.
* **Análisis eficiente:** Permite realizar consultas analíticas y resúmenes (agregaciones por columnas) de manera mucho más rápida que una base de datos por filas.
* **Registro de eventos:** Es el modelo adecuado para sistemas de monitoreo y logs industriales.

---

# Ejercicio 4

**Solución:** Base de datos NoSQL Documental

**Justificación:**
* **Esquema flexible:** Permite que cada artículo (documento) tenga campos diferentes según su tipo (galería, video, texto) sin alterar una tabla rígida.
* **Evolución rápida:** Facilita cambios frecuentes en el modelo de datos sin necesidad de migraciones costosas.
* **Gestión de contenidos:** Es el estándar para CMS y aplicaciones web modernas donde la información se estructura en formato similar a JSON.

---

# Ejercicio 5

**Solución:** Base de datos Relacional (SQL)

**Justificación:**
* **Transacciones críticas:** En escenarios bancarios es imperativo que las operaciones sean atómicas y duraderas; no se puede tolerar la pérdida de datos o inconsistencias temporales.
* **Integridad estricta:** Se requiere garantizar que el dinero descontado de una cuenta aparezca inmediatamente en la otra, algo que el modelo ACID asegura frente a la consistencia eventual de NoSQL.

---

# Ejercicio 6

**Solución:** Base de datos NoSQL de Grafos

**Justificación:**
* **Relaciones complejas:** El valor de los datos reside en las conexiones (quién conoce a quién, dispositivos compartidos), escenario donde los grafos son muy superiores a las tablas.
* **Análisis de redes:** Permite detectar patrones, comunidades y relaciones indirectas (amigos de amigos) de forma eficiente, algo muy costoso de hacer con SQL (múltiples JOINs).

---

# Ejercicio 7

**Solución:** Base de datos NoSQL Vectorial

**Justificación:**
* **Búsqueda por similitud:** Permite encontrar documentos basándose en el significado semántico y no solo en la coincidencia exacta de palabras clave.
* **Vectores numéricos:** Almacena la información como vectores matemáticos para calcular la cercanía entre conceptos, ideal para motores de búsqueda inteligentes.

---

# Ejercicio 8

**Solución:** Base de datos Relacional (SQL)

**Justificación:**
* **Estructura estable:** Cuando el modelo de datos es claro, bien definido y no cambia frecuentemente, SQL ofrece la mejor organización y consistencia.
* **Volumen moderado:** Sin problemas de escala masiva ni necesidad de distribución compleja, no se justifica la complejidad adicional o la pérdida de consistencia de un sistema NoSQL.