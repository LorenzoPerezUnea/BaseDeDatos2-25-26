# Introducción

Hasta este punto del curso hemos estudiado MongoDB principalmente desde tres perspectivas: modelado de datos, rendimiento de consultas y optimización mediante índices. Estas dimensiones son fundamentales para que una base de datos funcione correctamente y escale en volumen de información. Sin embargo, en un entorno real de producción estas capacidades por sí solas no son suficientes.

Un sistema que consulta rápido pero no controla el acceso a los datos puede convertirse en una vulnerabilidad crítica. Del mismo modo, una base de datos flexible que permite estructuras documentales variadas puede terminar almacenando información inconsistente si no se establecen mecanismos de validación.

Por esta razón, en esta clase introducimos una dimensión adicional del diseño de bases de datos: la seguridad y la integridad estructural. Esto implica comprender cómo MongoDB gestiona la identidad de los usuarios, cómo controla qué operaciones pueden realizar, y cómo puede imponer reglas sobre la estructura de los documentos almacenados.

En términos generales, esta parte de la clase aborda tres ideas fundamentales:

* Control de acceso mediante **autenticación y autorización**
* Aplicación del **principio de mínimo privilegio**
* Uso de **validación estructural con JSON Schema**

Estas capacidades permiten transformar una base de datos funcional en una base de datos preparada para entornos profesionales y de producción.

