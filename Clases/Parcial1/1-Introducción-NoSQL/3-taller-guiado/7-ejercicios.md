# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

R: Lo ideal es una base relacional SQL ya que se necesita asegurar consistencia.

### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

R: Se necesita una base de datos de tipo Clave-Valor que permite latencia mínima.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

R: Una base de datos de tipo Columnar que sirve para escritura masiva y consultas sobre grandes volumenes de datos.

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

R: Documental ya que permite flexibilidad.

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

R: Relacional SQL para guardar relaciones entre cuentas y transferencias.

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

R: Grafos para manejar relaciones complejas de forma eficiente.

### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

R: Vectorial, que permite realizar busquedas semánticas.

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

R: Relacional SQL que permita relaciones entre empleados y departamentos, asi manteniendolo lo suficientemente simple para la escala.