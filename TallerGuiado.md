## Ejercicio 1 – Base de datos relacional (SQL)

- Entidades bien estructuradas con relaciones claras (matrículas, asignaturas, profesores, actas).
- Necesidad de operaciones transaccionales fiables con propiedades ACID.
- Esquema estable y carga asumible con un sistema relacional clásico.

---

## Ejercicio 2 – Base de datos Clave–Valor (NoSQL)

- Cada registro se identifica principalmente por una clave (usuario, sesión).
- La información es sencilla, independiente y de vida corta.
- Lo más importante es la latencia muy baja y la capacidad de caducar datos automáticamente.

---

## Ejercicio 3 – Base de datos Columnar (NoSQL)

- Flujo continuo de datos de sensores con un número muy grande de registros.
- Consultas centradas en agregaciones por fecha, planta y tipo de sensor.
- Interesa optimizar lecturas analíticas y crecer fácilmente añadiendo nodos.

---

## Ejercicio 4 – Base de datos Documental (NoSQL)

- Los artículos no comparten un conjunto fijo de campos.
- El modelo de contenido cambia a menudo y se prefiere evitar migraciones de tablas.
- Cada artículo se puede guardar como un documento independiente con estructura flexible.

---

## Ejercicio 5 – Base de datos relacional (SQL)

- Operaciones críticas sobre dinero que requieren total precisión.
- Se deben garantizar transacciones completas o revertidas, sin estados intermedios visibles.
- Las relaciones entre cuentas y movimientos encajan muy bien en tablas relacionales.

---

## Ejercicio 6 – Base de datos de Grafos (NoSQL)

- El análisis se centra en quién se relaciona con quién y cómo.
- Se buscan rutas, conexiones indirectas y grupos dentro de la red de usuarios.
- El modelo de nodos y aristas simplifica consultas que en SQL exigirían muchos joins encadenados.

---

## Ejercicio 7 – Base de datos Vectorial (NoSQL)

- El objetivo es medir similitud de significado entre textos, no coincidencia exacta de términos.
- Los documentos y las consultas se representan mediante vectores numéricos (embeddings).
- Se necesitan índices especializados para búsquedas por cercanía en espacios de alta dimensión.

---

## Ejercicio 8 – Base de datos relacional (SQL)

- Esquema corporativo clásico con empleados y departamentos, fácil de modelar en tablas.
- Cantidad de datos moderada y estructura estable a largo plazo.
- Consultas bien definidas (informes, jerarquías simples) que un motor SQL resuelve de forma directa.
