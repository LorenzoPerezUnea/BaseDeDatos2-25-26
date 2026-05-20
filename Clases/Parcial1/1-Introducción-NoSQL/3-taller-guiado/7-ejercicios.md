# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.
Respuesta
Las entidades tienen relaciones claras, se exige consistencia total, las transacciones siguen ACID, el esquema es fijo y no se necesita gran escalado horizontal.


### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.
Respuesta 
Se accede a los datos por una clave única, no hay vínculos entre ellos, se prioriza rapidez, la información es temporal y no se hacen consultas complejas.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.
Respuestas 
Maneja enormes cantidades de datos, enfocada en análisis y estadísticas, predominan las lecturas, se buscan patrones generales y requiere escalabilidad horizontal.

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.
Respuestas 
Las entidades no tienen una estructura fija, el modelo cambia seguido, cada documento es independiente, permite consultas flexibles y evita cambios constantes de esquema.
### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.
Respuestas
Sistema altamente transaccional donde la inconsistencia es inaceptable, se necesita atomicidad y durabilidad, con relaciones claras entre datos críticos.
### Ejercicio 6
Lo más importante son las relaciones, se analizan conexiones directas e indirectas, las consultas recorren grafos y SQL sería poco eficiente por tantos joins.
Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.
Respuestas 

### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.
Respuesta s
Permite buscar por similitud de significado, no por coincidencia exacta, usa vectores y embeddings, ideal para trabajar con modelos de lenguaje.
### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.
Respuestas 
Modelo sencillo y estable, volumen manejable, relaciones bien definidas, consultas predecibles y NoSQL no aporta ventajas claras.
