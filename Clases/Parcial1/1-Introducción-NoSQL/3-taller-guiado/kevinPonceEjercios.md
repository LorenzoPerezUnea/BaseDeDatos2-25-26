# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

 #### basse de datos sql
- permite consitencia en los datos 
- permite trancaciones avanzadas 
- nodelo de datos estable (no cambia)


### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

#### Clave valor (cache)
- facilita Datos temporales
- gran velocidad de lectura (casi inmediato)
- no requiere relaciones complejas 

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

#### Columnares
- gran voulmen de datos
- proriza calculos analticos 
- escalavilidad horizontal a futuro

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

#### documental
- cambios continuos en la estrcutura 
- entidades indepndientes con campos variables

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

##### sql 
- require gran consitencia 
- fiablidad de datos
- transaciones para prevenir fallos

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

#### graphos 
- relaciones compeljas 
- proriza las relaciones ante las entidades 
- conexiones indirectas

### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

#### vectoriales
- propiza busqueda semantica
- busca simlitud y no igualdad 
-  integracion con modelos de ia

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

#### sql 
- modelo concitente
- relaciones claras y simples 
