# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

# Selección del tipo de base de datos

## Ejercicio 1  
**Tipo de base de datos recomendada:** Base de datos **relacional**

**Justificación:**  
El sistema debe gestionar matrículas, asignaturas, profesores y actas de notas, lo que implica entidades bien definidas y relaciones claras entre ellas. Además, se exige **consistencia fuerte** y **transacciones seguras**, especialmente durante los periodos de matrícula y en el registro de calificaciones.  
Las bases de datos relacionales garantizan propiedades **ACID**, integridad referencial y control transaccional, lo que resulta imprescindible para evitar incoherencias en las notas o matrículas.



## Ejercicio 2  
**Tipo de base de datos recomendada:** Base de datos **clave–valor**

**Justificación:**  
El sistema almacena preferencias de usuario, tokens de sesión y configuraciones temporales, accedidas siempre mediante una clave concreta. Se requiere acceso inmediato y eliminación automática tras inactividad, lo que encaja con el uso de **TTL (time-to-live)**.  
Las bases de datos clave–valor ofrecen muy baja latencia, simplicidad y son ideales para datos efímeros y de sesión.



## Ejercicio 3  
**Tipo de base de datos recomendada:** Base de datos **columnar**

**Justificación:**  
Se manejan millones de registros diarios de sensores y los analistas realizan consultas agregadas por día, planta y tipo de sensor. Este patrón es claramente analítico (OLAP).  
Las bases de datos columnares están optimizadas para **grandes volúmenes de datos** y **consultas de agregación**, permitiendo escanear solo las columnas necesarias y mejorar el rendimiento en informes históricos.


## Ejercicio 4  
**Tipo de base de datos recomendada:** Base de datos **documental**

**Justificación:**  
Cada artículo puede tener una estructura distinta y el modelo de datos cambia con frecuencia. Esto requiere un esquema flexible y capacidad para manejar campos opcionales y estructuras anidadas.  
Las bases de datos documentales permiten almacenar documentos con formatos variables (por ejemplo, JSON) sin necesidad de redefinir el esquema constantemente.



## Ejercicio 5  
**Tipo de base de datos recomendada:** Base de datos **relacional**

**Justificación:**  
El registro de transferencias bancarias exige que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.  
Las bases de datos relacionales proporcionan **atomicidad, consistencia, aislamiento y durabilidad (ACID)**, lo que las convierte en la opción adecuada para sistemas financieros críticos.



## Ejercicio 6  
**Tipo de base de datos recomendada:** Base de datos **de grafos**

**Justificación:**  
El sistema necesita analizar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos.  
Este tipo de consultas se basa en la **navegación por relaciones** y en el análisis de grafos, para lo cual las bases de datos de grafos son especialmente eficientes y expresivas.



## Ejercicio 7  
**Tipo de base de datos recomendada:** Base de datos **vectorial**

**Justificación:**  
El buscador debe encontrar documentos similares a una descripción escrita, aunque no coincidan exactamente las palabras utilizadas. Esto implica búsqueda por **similitud semántica**.  
Las bases de datos vectoriales permiten almacenar embeddings y realizar búsquedas por proximidad entre vectores, resolviendo este tipo de problema de forma eficiente.


## Ejercicio 8  
**Tipo de base de datos recomendada:** Base de datos **relacional**

**Justificación:**  
El sistema gestiona empleados, departamentos y jerarquías simples con un volumen de datos moderado y relaciones estables.  
Las bases de datos relacionales son adecuadas para este escenario, ya que permiten modelar relaciones bien definidas, mantener integridad referencial y realizar consultas estructuradas sin necesidad de soluciones más complejas.

