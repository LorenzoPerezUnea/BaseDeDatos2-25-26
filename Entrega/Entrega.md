# Resolución de ejercicios de bases de datos

## Ejercicio 1
**Tipo de base de datos:** Relacional (SQL)

**Justificación:**  
Los datos están altamente estructurados y relacionados. Se requiere consistencia fuerte y transacciones ACID para garantizar que las matrículas y las calificaciones se registren correctamente, incluso con múltiples usuarios concurrentes.

---

## Ejercicio 2
**Tipo de base de datos:** Clave–valor

**Justificación:**  
Permite acceso inmediato a los datos y soporta expiración automática. Es ideal para almacenar preferencias, tokens de sesión y configuraciones temporales que pueden eliminarse tras un tiempo de inactividad.

---

## Ejercicio 3
**Tipo de base de datos:** Columnar / Analítica (OLAP)

**Justificación:**  
Está diseñada para manejar grandes volúmenes de datos y realizar consultas agregadas eficientes. Es adecuada para análisis históricos por día, planta y tipo de sensor.

---

## Ejercicio 4
**Tipo de base de datos:** Orientada a documentos

**Justificación:**  
Ofrece flexibilidad en el esquema, permitiendo que cada documento tenga una estructura distinta. Es adecuada cuando el modelo de datos cambia con frecuencia.

---

## Ejercicio 5
**Tipo de base de datos:** Relacional (SQL)

**Justificación:**  
Las operaciones bancarias requieren transacciones completamente consistentes y seguras. Las bases de datos relacionales garantizan integridad, atomicidad y recuperación ante fallos.

---

## Ejercicio 6
**Tipo de base de datos:** Orientada a grafos

**Justificación:**  
Permite modelar y consultar relaciones complejas e indirectas de forma eficiente, facilitando la detección de comunidades y conexiones sospechosas.

---

## Ejercicio 7
**Tipo de base de datos:** Motor de búsqueda / orientada a texto

**Justificación:**  
Soporta búsquedas aproximadas y semánticas, permitiendo encontrar documentos similares aunque no coincidan exactamente las palabras utilizadas.

---

## Ejercicio 8
**Tipo de base de datos:** Relacional (SQL)

**Justificación:**  
El volumen es moderado y las relaciones son claras y estables, lo que hace que una base de datos relacional sea la opción más simple y adecuada.
