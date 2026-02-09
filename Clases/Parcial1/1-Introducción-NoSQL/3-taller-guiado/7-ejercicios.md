# Enunciados de los ejercicios

### Ejercicio 1

Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas.
Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

- Se opta por una base de datos relacional (SQL) porque el sistema maneja entidades claramente conectadas entre sí, como alumnos, asignaturas y profesores.
- Es escencial que las notas sean siempre correctas y coherentes, incluso si ocurre algún fallo durante la operación.
- Las matrículas requieren de transacciones fiables que cumplan con las propiedades ACID.
- Después de todo lo dicho podemos concluir que el esquema de datos es bastante estable y no se espera un crecimiento masivo que obligue a escalar horizontalmente.

### Ejercicio 2

Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales.
El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

- Se opta por una base de datos Clave-Valor(No SQL) ya que los datos acceden directamente mediante un identificador único.
- No existen relaciones entre la información almacenada y se busca la máxima rapidez de acceso.
- Las preferencias y tokens son datos temporales que pueden eliminarse automáticamente tras un periodo de inactividad.

### Ejercicio 3

Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento.
Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

- Se opta por una base de datos Columnar(No SQL) ya que se maneja una cantidad enorme de datos que crece de forma constante, lo que exige una solución escalable.
- Las consultas no se centran en registros individuales, si no en cálculos agregados y en estadísticas.

### Ejercicio 4

Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo.
Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

- Se opta por una base de datos Documental(No SQL) ya que cada artículo puede tener una estructura distinta.
- El modelo de datos cambia frecuentemente por lo que no sería conveniente ni eficiente redefinir los esquemas constantemente.
- Cada documento puede almacenar la información de un artículo de forma independiente.

### Ejercicio 5

Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

- Se opta por una base de datos relacional(SQL).
- Cada operación debe completarse por completo o no ejecutarse en absoluto.
- Las transacciones deben ser duraderas y seguras incluso ante caídas del sistema.

### Ejercicio 6

Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

- Se opta por una base de datos de grafos (No SQL).
- El objetivo principal es analizar las relaciones entre usuarios, mensajes y dispositivos.
- No solo importan las conexiones directas, sino también las indirectas y los patrones que se forman.

### Ejercicio 7

Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

- Se opta por una base de datos vectorial(No SQL).
- Este buscador no se basa en coincidencias exactas de palabras, sino en el significado del texto.
- Para ello se utilizan representaciones vectoriales que permiten medir similitud semántica.

### Ejercicio 8

Un sistema corporativo gestiona empleados, departamentos y jerarquías simples.
El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

- Se opta por una base de datos relacional (SQL).
- La estructura no cambia con el tiempo y las consultas son predecibles.
- Una base de datos relacional es suficiente y más sencilla de mantener.
