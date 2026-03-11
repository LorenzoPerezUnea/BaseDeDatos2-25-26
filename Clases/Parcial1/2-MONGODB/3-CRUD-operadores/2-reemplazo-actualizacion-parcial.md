# Naturaleza de la actualización en modelo documental: Diferencia entre reemplazo y actualización parcial

En bases relacionales, las actualizaciones modifican celdas específicas en tablas normalizadas.

En MongoDB, el documento es la unidad atómica de almacenamiento.

```mermaid
flowchart TD
    SQL[Tabla Relacional]
    SQL --> Fila
    Fila --> Columna1
    Fila --> Columna2

    Mongo[Documento]
    Mongo --> Campo1
    Mongo --> ObjetoEmbebido
    ObjetoEmbebido --> SubCampo
```

En MongoDB existen dos formas de modificar documentos:

### Reemplazo completo (replaceOne):

replaceOne elimina completamente la estructura previa.

```mermaid
flowchart LR
    DocumentoCon10Campos --> replaceOne
    replaceOne --> DocumentoCon3Campos
```

```js
db.cursos.replaceOne(
  { nombre: "Bases de Datos" },
  {
    nombre: "Bases de Datos",
    profesor: "Dr. Ramírez",
    creditos: 4
  }
)
```

* El documento anterior se elimina y se sustituye completamente.
* Si olvidamos campos, se pierden datos.

### Actualización parcial (updateOne):

updateOne mantiene la estructura no mencionada.

```mermaid
flowchart LR
    DocumentoOriginal --> $set
    $set --> DocumentoModificado
```

```js
db.cursos.updateOne(
  { nombre: "Bases de Datos" },
  { $set: { profesor: "Dr. Ramírez" } }
)
```

Solo se modifica el campo indicado.

### Diagrama conceptual

```mermaid
flowchart LR
    DocumentoOriginal --> ReemplazoCompleto
    DocumentoOriginal --> ActualizacionParcial
    ReemplazoCompleto --> NuevoDocumento
    ActualizacionParcial --> DocumentoModificado
```

