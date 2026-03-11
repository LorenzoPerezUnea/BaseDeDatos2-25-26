# Respaldo de bases de datos con mongodump

La herramienta mongodump permite generar un respaldo lógico de una base de datos. Este respaldo consiste en archivos BSON que contienen los documentos almacenados en cada colección.

Un comando típico de respaldo es el siguiente:

```BASH
mongodump --uri="mongodb://admin:admin123@localhost:27018" --out=backup_universidad
```

```BASH
mongodump  --out=backup_universidad
```

Este comando realiza las siguientes acciones:

* se conecta al servidor MongoDB
* recorre todas las bases de datos accesibles
* exporta cada colección a archivos BSON
* guarda los archivos en un directorio local

La estructura generada suele verse así:

```BASH
backup_universidad/
   universidad/
      cursos.bson
      cursos.metadata.json
      estudiantes.bson
      estudiantes.metadata.json
```

Cada colección produce dos archivos:

* .bson con los datos
* .metadata.json con información estructural

Si se desea respaldar únicamente una base de datos específica:

```BASH
mongodump \
--uri="mongodb://admin:admin123@localhost:27018" \
--db universidad \
--out backup_universidad
```

También es posible respaldar una colección específica:

```BASH
mongodump \
--uri="mongodb://admin:admin123@localhost:27018" \
--db universidad \
--collection cursos \
--out backup_cursos
```

Este tipo de operaciones permite generar copias selectivas de información.

