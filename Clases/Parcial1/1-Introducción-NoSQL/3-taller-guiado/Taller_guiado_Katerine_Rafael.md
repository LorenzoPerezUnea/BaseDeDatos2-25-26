# Enunciados de los ejercicios 
# Katerine Lisbeth Rafael Bourdierd

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

**Solución: SQL (Relacional)**

No puede existir una nota sin un alumno, ni un alumno matriculado en una carrera que no existe.

### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

**Solución: NoSQL (No Relacional)**

Solo se necesita escribirlo a todos lo más rápido posible en un cuaderno infinito.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

**Solución: NoSQL (No Relacional)**

Un artículo tiene fotos, otro tiene video, otro solo texto. Tendriamos muchas casillas vacías en los artículos que no tienen video. NoSQL te permite guardar cada artículo.

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

**Solución: NoSQL (No Relacional)**

Por que un artículo tiene fotos, otro tiene video, otro solo texto. Si usas SQL (Excel), tendrías muchas casillas vacías en los artículos que no tienen video. NoSQL te permite guardar cada artículo.

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

**Solución: SQL (Relacional)**

Es el caso clásico de seguridad. Si el dinero sale de tu cuenta, tiene que llegar a la otra. No puede "perderse en el camino" si se va la luz. SQL tiene mecanismos de seguridad (como una caja fuerte) para asegurar que la operación se hace completa o no se hace, pero nunca se queda a medias.

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

**Solución: NoSQL (No Relacional)**

Por qué aquí no importan tanto los datos personales, sino las flechas que unen a las personas.


### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

**Solución: NoSQL (No Relacional)**

Por qué SQL es muy literal, si buscas "Coche", te da "Coche". Pero aquí quieres que si buscas "Coche", el sistema entienda que "Automóvil" es casi lo mismo. Necesitas una base de datos que entienda conceptos, no solo letras exactas.

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

**Solución: SQL (Relacional)**

Por qué es el típico archivo de oficina. Tienes empleados, departamentos y jefes. La estructura casi nunca cambia y los datos caben perfectamente en una tabla.