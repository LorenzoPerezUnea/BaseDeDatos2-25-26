# Restauración de datos con mongorestore

La herramienta mongorestore permite reconstruir una base de datos a partir de los archivos generados por `mongodump`.

Ejemplo básico:

```BASH
mongorestore \ --drop
--uri="mongodb://admin:admin123@localhost:27017" \
backup_universidad
```

Este comando:

* lee los archivos BSON
* recrea las colecciones
* inserta nuevamente los documentos

El flujo completo de recuperación puede representarse así:

```mermaid
flowchart TD
A[Archivo BSON de respaldo] --> B[mongorestore]
B --> C[Reconstrucción de colecciones]
C --> D[Inserción de documentos]
D --> E[Base de datos restaurada]
```

Si queremos restaurar una colección específica:

```BASH
mongorestore \
--uri="mongodb://admin:admin123@localhost:27018" \
--nsInclude="universidad.cursos" \
backup_universidad
```

Esto resulta útil cuando solo una colección ha sido dañada o eliminada accidentalmente.

