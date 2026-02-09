# Soluciones a los Ejercicios de Clase: Bases de Datos

### Ejercicio 1: Gestión Académica
- **Elección:** **Base de Datos Relacional (SQL)**
- **Justificación:**
  Lo fundamental en este escenario es la consistencia de los datos. La relación entre alumnos, materias cursadas y pagos debe ser exacta; no hay margen para errores como registros duplicados o datos incompletos. El modelo relacional garantiza las propiedades ACID, asegurando que cualquier operación compleja (como cerrar un acta) se complete totalmente o se cancele, protegiendo la integridad de la información académica.

### Ejercicio 2: App Móvil (Sesiones y Caché)
- **Elección:** **NoSQL Clave-Valor**
- **Justificación:**
  El objetivo crítico es la velocidad inmediata. Para verificar la identidad de un usuario en cada petición, necesitamos un acceso casi instantáneo que no se consigue con consultas complejas, sino con una búsqueda directa por identificador (clave). Además, la funcionalidad nativa de expiración de datos (TTL) es ideal para gestionar sesiones temporales sin necesidad de mantenimiento manual.

### Ejercicio 3: Sensores Industriales (IoT)
- **Elección:** **NoSQL Columnar (Wide-Column)**
- **Justificación:**
  Este escenario requiere manejar una ingesta masiva de información en tiempo real. Estas bases de datos están optimizadas para escrituras de alta velocidad y gran volumen. A nivel de lectura, su arquitectura permite realizar análisis eficientes sobre atributos específicos (por ejemplo, extraer solo la columna de "presión" de millones de registros) sin la sobrecarga que implicaría leer filas enteras en otros sistemas.

### Ejercicio 4: CMS (Gestión de Contenidos)
- **Elección:** **NoSQL Documental**
- **Justificación:**
  La naturaleza del contenido web es polimórfica y cambiante. Un post puede tener videos, otro solo texto y otro metadatos personalizados. Un esquema rígido (SQL) obligaría a tener tablas llenas de campos nulos o estructuras complejas. El modelo documental permite almacenar cada publicación como un objeto JSON independiente, adaptándose a la estructura que necesite cada contenido sin romper el esquema general.

### Ejercicio 5: Transacciones Bancarias
- **Elección:** **Base de Datos Relacional (RDBMS)**
- **Justificación:**
  En operaciones financieras, la prioridad absoluta es la exactitud y la atomicidad. Al mover dinero de una cuenta a otra, el sistema debe garantizar que ambas cuentas se actualicen simultáneamente en una transacción "todo o nada". Los modelos NoSQL suelen ofrecer "consistencia eventual", lo cual es inaceptable para un banco donde el saldo debe ser exacto en todo momento.

### Ejercicio 6: Detección de Fraude y Red Social
- **Elección:** **NoSQL de Grafos**
- **Justificación:**
  El valor de estos datos reside en la topología de la red, es decir, en cómo se conectan las entidades entre sí. Para descubrir patrones de fraude o recomendar contactos, es necesario navegar profundamente por las relaciones. Las bases de datos de grafos hacen esto de forma nativa e instantánea, evitando las costosas operaciones de unión (JOINs) que ralentizarían un sistema relacional.

### Ejercicio 7: Buscador Semántico
- **Elección:** **Base de Datos Vectorial**
- **Justificación:**
  Para entender el significado detrás de una consulta y no solo buscar palabras exactas, necesitamos trabajar con *embeddings*. Este modelo transforma el texto en coordenadas numéricas (vectores) en un espacio multidimensional. La base de datos vectorial es la única diseñada específicamente para indexar y calcular la proximidad entre estos puntos de forma eficiente, permitiendo búsquedas por similitud de contexto.

### Ejercicio 8: Gestión Corporativa Simple
- **Elección:** **Base de Datos Relacional**
- **Justificación:**
  Para problemas estándar, soluciones estándar. Al tener un volumen de datos controlable y una estructura organizativa clara y poco cambiante, no hace falta recurrir a modelos complejos. SQL proporciona la estabilidad, las herramientas de reporte y la facilidad de uso ideales para aplicaciones de gestión interna donde la consistencia es más importante que la escalabilidad masiva.