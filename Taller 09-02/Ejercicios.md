# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

### Respuesta

Base de Datos Relacional (SQL) como PostgreSQL. Explicación: Garantiza propiedades ACID (Atomicidad, Consistencia, Aislamiento y Durabilidad). En un sistema de actas y matrículas, no puedes permitir que una nota se registre a medias o que un alumno se matricule en una asignatura sin plazas.

### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

### Respuesta

Base de Datos en Memoria (Key-Value) como Redis. Explicación: Almacena los datos en la RAM para un acceso de milisegundos. Permite configurar un TTL (Time To Live), lo que automatiza el borrado de sesiones inactivas por seguridad.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

### Respuesta

Base de Datos de Series Temporales (Time-Series) como InfluxDB o ClickHouse. Explicación: Están optimizadas para insertar millones de registros por segundo y realizar consultas de agregación (medias, máximos, mínimos) sobre ejes temporales de forma masiva y eficiente.

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

### Respuesta

Base de Datos Documental (NoSQL) como MongoDB. Explicación: Utiliza esquemas flexibles (JSON/BSON). Esto permite que cada artículo tenga campos diferentes sin necesidad de reestructurar toda la base de datos cada vez que el modelo cambia.

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

### Respuesta

Base de Datos Relacional con soporte Transaccional Robusto (ej. SQL Server o PostgreSQL). Explicación: En banca, la integridad es crítica. Se requiere un sistema que asegure que si una cuenta se debita, la otra se acredita en la misma transacción atómica, evitando que el dinero "desaparezca" en un crash.

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

### Respuesta

Base de Datos de Grafos como Neo4j. Explicación: En lugar de tablas, usa nodos y relaciones. Es la herramienta óptima para recorrer conexiones complejas (amigo de un amigo) y detectar patrones de fraude o comunidades en redes sociales rápidamente.

### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

### Respuesta

Base de Datos de Vectores (Vector DB) como Pinecone o Milvus. Explicación: Convierte el texto en coordenadas matemáticas (embeddings). Esto permite realizar búsquedas semánticas, encontrando documentos por "significado" o similitud conceptual en lugar de coincidencias de palabras exactas.

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

### Respuesta

Base de Datos Relacional (SQL) básica como MySQL o MariaDB. Explicación: Para estructuras jerárquicas estables y volúmenes moderados, el modelo relacional es el estándar más fiable, fácil de mantener y con mejor soporte para consultas de administración corporativa.

