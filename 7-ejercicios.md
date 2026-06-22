Solución ejercicios de clase

### Ejercicio 1: Gestión Académica 
* **Elección:** **Base de Datos Relacional**
* **El razonamiento:**
    El factor decisivo aquí es la integridad referencial. Una matrícula universitaria funciona como un contrato estricto entre alumno, asignatura y pagos; no podemos permitirnos datos "huérfanos" o inconsistentes. Necesitamos las garantías ACID para asegurar que, si el sistema falla mientras se guarda un acta de notas, no se queden registros a medias. 

### Ejercicio 2: App Móvil (Sesiones y Caché)
* **Elección:** **NoSQL Clave-Valor**
* **El razonamiento:**
    La prioridad  es la baja latencia. El usuario no va a esperar segundos a que la app verifique su sesión; necesitamos tiempos de respuesta en milisegundos. Este modelo es perfecto porque permite recuperar el dato (token) directamente por su ID sin complicaciones. Además, funcionalidades como el Time To Live permiten que los datos viejos se "autodestruyan" sin que tengamos que programar tareas de limpieza complejas.

### Ejercicio 3: Sensores Industriales (IoT)
* **Elección:** **NoSQL Columnar (Wide-Column)**
* **El razonamiento:**
    Estamos ante un caso de libro de Big Data. El reto es la velocidad de escritura (ingesta) de millones de datos por segundo. Las bases de datos columnares son excelentes escribiendo masivamente y, lo más importante, son muy eficientes leyendo datos para analítica: si queremos la temperatura media del último año, la base de datos lee solo la columna temperatura sin perder tiempo cargando el resto de la fila.

### Ejercicio 4: CMS (Gestión de Contenidos)
* **Elección:** **NoSQL Documental**
* **El razonamiento:**
    El problema principal es la variedad de los datos. Un artículo puede ser solo texto, otro tener una galería de fotos y otro un video incrustado. Forzar esto en una tabla SQL resultaría en muchas columnas vacías NULL o un diseño rígido difícil de mantener. El modelo documental (JSON) nos da la flexibilidad de guardar objetos con estructuras diferentes en la misma colección, facilitando la evolución rápida del producto.

### Ejercicio 5: Transacciones Bancarias
* **Elección:** **Base de Datos Relacional (RDBMS)**
* **El razonamiento:**
    Cuando hay dinero de por medio, la atomicidad no es negociable. Una transferencia implica restar saldo en A y sumar en B; ambas cosas deben ocurrir simultáneamente o no ocurrir ninguna. Los modelos NoSQL (orientados a BASE) suelen sacrificar esta consistencia inmediata a favor del rendimiento, un riesgo que un banco no puede asumir en su núcleo transaccional.

### Ejercicio 6: Detección de Fraude y Red Social
* **Elección:** **NoSQL de Grafos**
* **El razonamiento:**
    Aquí el valor no está en el dato individual, sino en la relación. Para detectar fraude (ej. anillos de cuentas falsas) o sugerir amigos, necesitamos recorrer conexiones ("amigo del amigo") muy rápido. Intentar esto en SQL requiere múltiples JOINs que degradan el rendimiento exponencialmente. Los grafos están matemáticamente optimizados para saltar entre nodos instantáneamente.

### Ejercicio 7: Buscador Semántico
* **Elección:** **Base de Datos Vectorial**
* **El razonamiento:**
    Las bases de datos tradicionales buscan coincidencias exactas de palabras. Aquí necesitamos buscar por significado o contexto (similitud semántica).  Para lograrlo, convertimos el texto en vectores numéricos y calculamos la distancia matemática entre ellos. Solo una base de datos vectorial puede indexar y comparar estas representaciones multidimensionales de forma eficiente.

### Ejercicio 8: Gestión Corporativa Simple
* **Elección:** **Base de Datos Relacional**
* **El razonamiento:**
    A veces, la solución clásica es la mejor. Dado que el volumen de datos es bajo, la jerarquía es simple y estable, y no hay requisitos extraños de escalabilidad. SQL ofrece la mejor relación entre facilidad de mantenimiento, robustez y estandarización para este tipo de aplicaciones administrativas.
