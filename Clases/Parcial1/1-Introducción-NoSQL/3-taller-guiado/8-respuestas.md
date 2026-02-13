
### Ejercicio 1: Universidad (Matrículas y Actas)

*Elección:* **SQL (Relacional)**

**¿Por qué esta?** El enunciado exige **consistencia fuerte** y **transacciones seguras**. En un sistema de actas de notas y matrículas, no puede haber errores de "consistencia eventual" (donde un dato tarda en actualizarse). SQL garantiza ACID (Atomicidad, Consistencia, Aislamiento y Durabilidad).

**¿Por qué no las otras?** 
    *   **NoSQL (BASE):** Priorizan disponibilidad sobre consistencia; podrías tener a un alumno matriculado en una clase sin cupo por un retraso en la sincronización.
    *   **Clave-Valor/Documental:** No gestionan las relaciones complejas entre alumnos, profesores y materias de forma tan robusta y segura como SQL.

----
### Ejercicio 2: Aplicación móvil (Sesiones y Preferencias)
*Elección:* **Clave–Valor (Ej. Redis)**

**¿Por qué esta?** Se pide **acceso inmediato** (baja latencia) y **caducidad automática** (TTL). Es el caso de uso de libro para una sesión de usuario donde buscas por un ID y obtienes el valor al instante.

**¿Por qué no las otras?**
    *   **SQL:** Es demasiado lento y pesado para tokens de sesión; no tiene gestión nativa de expiración de datos tan eficiente.
    *   **Documental:** Aunque serviría, es más compleja de lo necesario si solo vas a buscar por una clave única.

----
### Ejercicio 3: Sensores industriales (Análisis histórico)
*Elección:* **Columnar (Ej. Cassandra / HBase)**

**¿Por qué esta?** El volumen es masivo ("millones de registros diarios") y el uso es **analítico** (resúmenes, promedios por día o planta). Las bases columnares son óptimas para **agregaciones** sobre grandes volúmenes de datos históricos.

**¿Por qué no las otras?**
    *   **SQL:** Colapsaría con el volumen de escrituras y las consultas de agregación sobre millones de filas serían muy lentas.
    *   **Grafos/Vectoriales:** No tienen sentido aquí porque no buscamos ni relaciones complejas ni similitudes semánticas.

----
### Ejercicio 4: Gestión de Contenidos (CMS flexible)
*Elección:* **Documental (Ej. MongoDB)**

**¿Por qué esta?** La palabra clave es **esquema dinámico** o flexible. Cada artículo tiene campos distintos (video, galería, texto) y el modelo cambia con frecuencia. Los documentos (JSON/BSON) permiten guardar estructuras diferentes en la misma colección.

**¿Por qué no las otras?**
    *   **SQL:** Obligaría a hacer migraciones constantes de tablas (`ALTER TABLE`) o tener muchísimas columnas con valores nulos (poco eficiente).
    *   **Clave-Valor:** No permitiría hacer búsquedas complejas (ej. "buscar artículos que tengan video").

----
### Ejercicio 5: Banco (Transferencias bancarias)

*Elección:* **SQL (Relacional)**

**¿Por qué esta?** Es el escenario crítico de **integridad transaccional**. Si transfieres dinero de A a B, la resta en A y la suma en B deben ocurrir sí o sí como una única unidad. SQL es el estándar para asegurar que "nunca se pierda dinero".

**¿Por qué no las otras?**
    *   **Casi todas las NoSQL:** Están diseñadas para escalar horizontalmente a costa de relajar la consistencia inmediata. En un banco, la "consistencia eventual" (que el saldo aparezca bien más tarde) es inaceptable.

----
### Ejercicio 6: Red Social (Detección de fraude y comunidades)
*Elección:* **Grafos (Ej. Neo4j)**

**¿Por qué esta?** El foco está en **relaciones indirectas** y conexiones de segundo o tercer nivel (ej. "Usuario A comparte dispositivo con Usuario B que es amigo de un estafador"). Los grafos tratan las relaciones como ciudadanos de primera clase.

**¿Por qué no las otras?**
    *   **SQL:** Requeriría muchísimos `JOINs`, lo que haría la consulta lentísima e imposible de programar para niveles profundos.
    *   **Columnar/Clave-Valor:** No están diseñadas para navegar a través de conexiones entre datos.

----
### Ejercicio 7: Buscador Interno (Búsqueda semántica)

*Elección:* **Vectorial (Ej. Pinecone / Weaviate)**

**¿Por qué esta?** Se busca **similitud semántica** (por significado), no por coincidencia exacta de palabras. Estas bases usan *embeddings* para entender que "hogar" y "casa" son conceptos cercanos.

**¿Por qué no las otras?**
    *   **SQL/Documental:** Usan búsquedas de texto plano o índices invertidos. Si buscas "felino" y el documento dice "gato", una base de datos tradicional no lo encontraría a menos que definas sinónimos manualmente.

----

### Ejercicio 8: Sistema Corporativo (Empleados y Jerarquías)

*Elección:* **SQL (Relacional)**

**¿Por qué esta?** El volumen es **moderado**, la estructura es **estable** (empleados, departamentos) y las relaciones están bien definidas. No hay necesidad de la complejidad o escalabilidad masiva de NoSQL.

**¿Por qué no las otras?**
    *   **NoSQL (cualquiera):** Sería "matar moscas a cañonazos". Si el modelo no va a cambiar y los datos caben perfectamente en tablas, SQL es la opción más eficiente, madura y fácil de mantener.
