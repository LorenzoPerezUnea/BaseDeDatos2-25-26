# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

En esta usaria una base de datos relacional ya que se necesitan propiedades ACID (Atomicidad, Consistencia, Aislamiento y Durabilidad). No puedes permitir que un alumno se matricule en una asignatura sin plazas o que una nota se pierda a medias. La consistencia fuerte es innegociable aquí.


### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

CLAVE VALOR.

Buscas latencia mínima (acceso inmediato). Estos sistemas permiten definir un TTL (Time To Live) para que los datos caduquen y se borren solos tras la inactividad.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.


Orientada a columnas.

Están diseñadas para manejar volúmenes masivos de escritura y realizar consultas analíticas rápidas sobre columnas específicas (ej. "media de temperatura de la planta A").

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

Documental.

Utilizan esquemas flexibles (JSON/BSON). Al no tener un esquema rígido, puedes añadir campos nuevos (como "galería" o "vídeo") a unos documentos sin afectar a los anteriores.

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

Relacional

Es el caso de uso clásico de las transacciones SQL. Si restas 100€ de la cuenta A y falla el sistema antes de sumarlos a la B, la base de datos debe hacer un rollback automático para que el dinero no desaparezca.

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

Grafos

En lugar de tablas, usa nodos y relaciones. Es ideal para encontrar "amigos de amigos" o detectar fraude (conexiones sospechosas) mediante el recorrido de saltos entre nodos, algo que en SQL sería una pesadilla de JOINs.


### Ejercicio 7


Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.


Busqueda Vectorial

Permiten almacenar "embeddings" (representaciones numéricas del significado). Esto permite encontrar documentos por contexto o similitud, no solo por palabras clave exactas.

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

Relacional

Para datos estructurados, estables y de volumen moderado, el modelo relacional es el más eficiente y fácil de mantener. Las jerarquías se resuelven bien con claves foráneas simples.