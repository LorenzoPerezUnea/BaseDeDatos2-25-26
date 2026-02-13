# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

Se necesita una base de datos SQL porque existen relaciones bien definidas enter entidades y el modelo de datos es estructurado.

### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

Lo adecuado es usar una base de datos NoSql pues requiere acceso directo por identificador y no existen relaciones entre los datos.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

NoSQL porque tiene un volumen muy elevado de datos y es necesario una escalabilidad horizontal.

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

NoSQL porque existe una estructura variable entre entidades y hay necesidad de consultas felexibes por campos.

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

SQL porque existe un modelo relacional claro y hay necesidad de cumplir con ACID.

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

NoSQL porque las relaciones tienen significados propio y en este caso SQL requiriría multiples JOIN complejos.

### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

NoSQL porque existe una comparacion aproximada, no exacta y existe integracion con modelos de lenguaje.

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

SQL porque tiene un modelo de datos simple y bien definido y un volumen controlado.

