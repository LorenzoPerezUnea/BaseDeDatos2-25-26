# Introducción general

A partir de este momento vamos a empezar a trabajar con una forma distinta de entender los datos.

Hasta ahora hemos utilizado modelos donde la información se organiza en estructuras bastante claras: tablas en bases de datos relacionales y documentos en bases de datos NoSQL.

Ambos modelos funcionan muy bien cuando el problema consiste en almacenar información y recuperarla bajo ciertas condiciones. Pero en muchos sistemas reales, lo verdaderamente importante no es solo el dato en sí, sino cómo ese dato se relaciona con otros.

Aquí es donde entran las bases de datos de grafos. Este tipo de sistemas no está diseñado solo para guardar información, sino para representar conexiones de forma directa y natural.

Durante este bloque no solo vamos a aprender una nueva tecnología. Vamos a cambiar la forma en la que pensamos los datos.

### Pequeño ejercicio mental.

Imagina que tienes que diseñar el backend de una red social sencilla. No hace falta código, solo pensar en cómo guardarías la información.

Responde mentalmente a estas preguntas:

* ¿Dónde guardarías a los usuarios?
* ¿Cómo representarías que dos usuarios son amigos?
* ¿Cómo guardarías publicaciones y comentarios?

Lo más probable es que hayas pensado en tablas:

* usuarios
* amistades
* publicaciones
* comentarios

Este punto de partida es correcto.

