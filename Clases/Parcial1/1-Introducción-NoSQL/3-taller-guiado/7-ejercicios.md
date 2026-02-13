# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

Se necesita uan base de datos SQL relacional. Hay que administrar las entidades y sus relaciones, y tambien ocupamos tansacciones que cumplan los requirimientos ACID. La estructura tiene que ser consistente, estructurada y no veo necesidad de escalar horizontalmente la misma.

### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

Necesitaremos un identificador por token, cosa simple ya que solo necesitariamos comprobar ello. No hay relacion alguna entre los datos, aparte estos expiran asi que debemos darle prioridad a la velocidad de procesamiento. Claramente es mejor una Base de datos No-SQL Clave-Valor.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

Existen millones de datos, ya que la empresa se dedica a revisar mediante consultas estos datos en resumenes y estaditicas. Aqui ve necesario escalar horizontalmente ya que necesitaremos dar un enfoque grupo. Una Base de datos columnar tipo No-SQL estaria bien

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

Aqui deberemos usar una base de datos No-SQL documental. Debido a que la estructura puede variar con frecuencia entre las entidades, las consultas deben ser flexibles y por eso debemo sevitar migrarciones del esquema.

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

Una base de datos SQL recional es apropiado. Se ocupan bastante las transacciones, los datos no pueden cambiar y necesitan claridad. Además de claro definir bien la relacion que hay entre cada una de las entidades, esto no puede cambiar.

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

Necesitaremos una base de datos de grafos No-SQL. Aqui es mejor ya que si no recorrieramos la base de datos habria que hacer muchas uniniones. El peso de esta base de datos enta en elas relaciones entre entidades no las entidades en sí.

### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

Deberias ser una base de datos no vectorial.

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

Aqui una Base de datos normal y corriente, relacional SQL.
