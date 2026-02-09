# Resolución de Ejercicios: Elección de Base de Datos

A continuación se detalla la elección del tipo de base de datos para cada caso de uso propuesto, junto con la justificación técnica basada en las necesidades de consistencia, estructura de datos y escalabilidad.

## Ejercicio 1: Gestión Universitaria
**Solución: Base de Datos Relacional (SQL)**

* **Justificación:**
    * Existen relaciones bien definidas y rígidas entre las entidades (Alumnos, Asignaturas, Profesores).
    * Se requiere **consistencia fuerte** en todo momento (las notas no pueden ser inconsistentes).
    * Las transacciones deben cumplir las propiedades **ACID** (Atomicidad, Consistencia, Aislamiento, Durabilidad) para asegurar la integridad de las matrículas.
    * El modelo de datos es estable y no requiere cambios frecuentes de estructura.

## Ejercicio 2: App Móvil (Sesiones y Preferencias)
**Solución: Base de Datos Clave–Valor (NoSQL)**

* **Justificación:**
    * El patrón de acceso es directo por identificador (token o ID de usuario).
    * No existen relaciones complejas entre los datos almacenados; son datos aislados.
    * Se prioriza la **velocidad extrema** (baja latencia) sobre la complejidad de consulta.
    * Los datos (tokens de sesión) son temporales y pueden beneficiarse de funcionalidades como TTL (Time To Live) para expiración automática.

## Ejercicio 3: Sensores Industriales (Analytics)
**Solución: Base de Datos Columnar (NoSQL)**

* **Justificación:**
    * Se maneja un volumen masivo de datos (Big Data) con un crecimiento constante.
    * Las consultas son analíticas (agregaciones, resúmenes, medias), donde este modelo es mucho más eficiente que el relacional al leer solo las columnas necesarias.
    * El interés reside en encontrar patrones globales y tendencias históricas, no en recuperar registros individuales.
    * Requiere alta escalabilidad horizontal para soportar la ingesta masiva de escritura.

## Ejercicio 4: Sistema de Gestión de Contenidos (CMS)
**Solución: Base de Datos Documental (NoSQL)**

* **Justificación:**
    * La estructura de los datos es variable entre entidades (un artículo tiene video, otro solo texto, otro galería).
    * El modelo de datos cambia con frecuencia, requiriendo un esquema flexible (schema-less) para evitar migraciones costosas.
    * Cada entidad (artículo) es autocontenida y se recupera generalmente completa.
    * Permite consultas flexibles y ricas sobre cualquier campo del documento.

## Ejercicio 5: Sistema Bancario
**Solución: Base de Datos Relacional (SQL)**

* **Justificación:**
    * Es un dominio crítico donde la integridad de los datos es obligatoria; no se puede permitir la pérdida de dinero ni inconsistencias.
    * Se requiere atomicidad y durabilidad estricta (ACID) en las transacciones.
    * El modelo relacional entre cuentas, clientes y movimientos es claro y estable.
    * La consistencia eventual (típica de NoSQL BASE) no es aceptable en escenarios financieros.

## Ejercicio 6: Red Social (Detección de Fraude/Comunidades)
**Solución: Base de Datos de Grafos (NoSQL)**

* **Justificación:**
    * El valor principal de los datos reside en las **relaciones** y conexiones entre las entidades, más que en las entidades mismas.
    * Se necesita analizar conexiones indirectas (amigos de amigos, dispositivos compartidos) y patrones complejos de red.
    * Las consultas se basan en recorridos (traversals) y caminos, operaciones que en SQL requerirían múltiples JOINS costosos e ineficientes.

## Ejercicio 7: Buscador Semántico
**Solución: Base de Datos Vectorial (NoSQL)**

* **Justificación:**
    * La búsqueda se basa en la **similitud semántica** (significado) y no en la coincidencia exacta de palabras clave.
    * Se requiere almacenamiento y consulta de embeddings (representaciones vectoriales numéricas) generados por modelos de IA.
    * Las operaciones principales son comparaciones matemáticas de distancia (aproximadas), algo que SQL o NoSQL tradicional no resuelven eficientemente.

## Ejercicio 8: Sistema Corporativo Simple (RRHH)
**Solución: Base de Datos Relacional (SQL)**

* **Justificación:**
    * El modelo de datos (empleados, departamentos) es simple, jerárquico y está bien definido.
    * El volumen de datos es moderado y controlado, sin necesidad de escalar masivamente.
    * Las relaciones son estables en el tiempo.
    * No se justifica la complejidad de implementación y mantenimiento de una solución NoSQL para un problema estándar ya resuelto eficazmente por SQL.
