# 📚 Resolución de Ejercicios - Base de Datos 2

### Ejercicio 1: Universidad (Matrículas y Notas)
* **Modelo:** Relacional (SQL).
* **Justificación:** Requiere consistencia fuerte y transacciones seguras (ACID) para asegurar que las notas y matrículas sean exactas y no se pierdan datos.

### Ejercicio 2: Preferencias y Sesiones
* **Modelo:** NoSQL Clave-Valor.
* **Justificación:** Necesita acceso inmediato y velocidad extrema. Permite usar TTL para que los tokens de sesión se eliminen automáticamente tras la inactividad.

### Ejercicio 3: Sensores Industriales
* **Modelo:** NoSQL Columnar.
* **Justificación:** Ideal para grandes volúmenes de datos (Big Data). Permite realizar consultas analíticas e informes históricos de forma eficiente sobre millones de registros.

### Ejercicio 4: Gestión de Contenidos (CMS)
* **Modelo:** NoSQL Documental.
* **Justificación:** Ofrece flexibilidad total de esquema (JSON). Cada artículo puede tener campos distintos sin necesidad de una estructura rígida.

### Ejercicio 5: Transferencias Bancarias
* **Modelo:** Relacional (SQL).
* **Justificación:** Es un caso crítico donde la atomicidad es vital para garantizar que el dinero nunca se pierda y que las operaciones sean totalmente consistentes.

### Ejercicio 6: Red Social
* **Modelo:** NoSQL de Grafos.
* **Justificación:** Optimizado para gestionar relaciones complejas, detectar comunidades y encontrar conexiones indirectas entre usuarios y dispositivos.

### Ejercicio 7: Buscador Semántico
* **Modelo:** NoSQL Vectorial.
* **Justificación:** Permite realizar búsquedas por similitud de conceptos (contexto) en lugar de coincidencias exactas de palabras clave.

### Ejercicio 8: Jerarquías Corporativas
* **Modelo:** Relacional (SQL).
* **Justificación:** El volumen es moderado y las relaciones son fijas y estables en el tiempo, por lo que una estructura de tablas estándar es suficiente.

