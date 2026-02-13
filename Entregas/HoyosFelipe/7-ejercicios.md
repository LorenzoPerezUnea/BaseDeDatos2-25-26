# Enunciados de los ejercicios-RESPUESTAS

### Ejercicio 1

Pensaría que lo mejor acá es usar una base de datos relacional (tipo PostgreSQL o MySQL).
Digamos que en una universidad las notas, matrículas y actas no pueden quedar a medias, todo tiene que cumplirse sí o sí.
Las bases relacionales manejan muy bien las transacciones ACID, así que si algo falla, se deshace todo y no quedan datos inconsistentes. Para calificaciones eso es clave.

### Ejercicio 2

Yo diría que acá encaja mejor una base de datos clave-valor, como Redis.
Pensaría que lo importante es la velocidad y que los datos no duran para siempre.
Redis permite guardar tokens y preferencias en memoria y además definir tiempos de expiración, así que se borran solos cuando ya no se usan. Ideal para sesiones.

### Ejercicio 3

Digamos que con millones de registros diarios, una base relacional normal se queda corta.
Pensaría que lo mejor sería una base de datos orientada a columnas, tipo ClickHouse o BigQuery.
Estas están pensadas para análisis y consultas agregadas, como resúmenes por día, planta o sensor, y además escalan muy bien con grandes volúmenes de datos históricos.

### Ejercicio 4

Acá yo pensaría directamente en una base de datos documental como MongoDB.
Digamos que cada artículo puede tener campos distintos y eso cambia todo el tiempo.
Con documentos no hace falta un esquema fijo, así que es mucho más flexible para manejar artículos con texto, videos, galerías, etc., sin romper nada cada vez que cambia el modelo.

### Ejercicio 5

Pensaría que lo mejor, sin duda, es una base de datos relacional fuerte, con soporte total de transacciones.
Digamos que en un banco no puede desaparecer dinero ni duplicarse.
Las bases relacionales garantizan consistencia total, y si hay un fallo en medio de una transferencia, la operación se revierte completa.

### Ejercicio 6

Yo diría que acá lo más lógico es una base de datos de grafos, como Neo4j.
Pensaría que las relaciones son lo más importante: quién conoce a quién, conexiones indirectas, dispositivos compartidos, etc.
Las bases de grafos permiten recorrer relaciones complejas fácilmente y detectar patrones sospechosos o comunidades.

### Ejercicio 7

Pensaría que lo mejor es un motor de búsqueda con soporte semántico, como Elasticsearch o algún sistema con búsqueda vectorial.
Digamos que el usuario no siempre va a escribir las mismas palabras que están en el documento.
Este tipo de bases permiten encontrar textos similares en significado, no solo por coincidencia exacta de palabras.

### Ejercicio 8

Acá yo pensaría que una base de datos relacional clásica es más que suficiente.
Digamos que el volumen no es enorme, las relaciones son claras (empleados, departamentos, jerarquías simples) y no cambian mucho.
Las relacionales manejan esto de forma ordenada, clara y sin complicaciones innecesarias.

