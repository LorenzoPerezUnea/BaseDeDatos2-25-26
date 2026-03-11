# Roles predefinidos en MongoDB

MongoDB incluye una serie de roles estándar que cubren la mayoría de los casos de uso.

Entre los más comunes se encuentran:

* read
  * Permite consultar documentos
  * No permite modificaciones
* readWrite
  * Permite insertar
  * Permite actualizar
  * Permite eliminar
* dbAdmin
  * Permite administrar índices
  * Permite ejecutar operaciones administrativas
* clusterAdmin
  * Permite administrar todo el cluster

Tabla conceptual de permisos:

| Rol          | Lectura  | Escritura | Administración |
| -------------- | ---------- | ----------- | ----------------- |
| read         | Sí      | No        | No              |
| readWrite    | Sí      | Sí       | No              |
| dbAdmin      | Limitada | Limitada  | Sí             |
| clusterAdmin | Sí      | Sí       | Sí             |

En sistemas profesionales, los roles se asignan cuidadosamente para evitar privilegios innecesarios.

