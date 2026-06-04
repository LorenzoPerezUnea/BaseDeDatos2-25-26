# EJERCICIO 1 — Colección de Cursos

### ENUNCIADO

Se desea modelar una pequeña base de datos para cursos universitarios.

1. Crear una base de datos llamada: Universidad
2. Crear una colección llamada: cursos
3. Insertar manualmente 3 documentos con la siguiente estructura:

* nombre del curso
* profesor
* número de créditos
* lista de estudiantes inscritos (array de strings)
* activo (boolean)

Ejemplo de valores (no copiar literal, pueden variar):

* Bases de Datos
* Programación Web
* Inteligencia Artificial

4. Realizar las siguientes consultas desde el buscador de Mongo Express:

* Mostrar todos los cursos activos
* Mostrar los cursos con más de 3 créditos
* Mostrar los cursos  3 créditos o más
* Mostrar los cursos donde esté inscrito un estudiante específico

### Solución

### jsons de cursos

* [Curso 1.](json/4-curso-1.json)
* [Curso 2.](json/5-curso-2.json)
* [Curso 3.](json/6-curso-3.json)

### condiciones a ejecutar

* Mostrar todos los cursos activos: { "activo": true }
* Mostrar los cursos con más de 3 créditos: { "creditos": { "$gt": 3 } }
* Mostrar los cursos  3 créditos o más: { "creditos": { "$gte": 3 } }
* Mostrar los cursos donde esté inscrito un estudiante específico: { "estudiantes": "Ana" }

