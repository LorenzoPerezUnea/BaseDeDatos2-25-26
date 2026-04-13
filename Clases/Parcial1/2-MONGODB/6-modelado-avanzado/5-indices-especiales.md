# Índices especiales

MongoDB no solo tiene índices estándar.

### TTL (Time To Live)

Permite eliminar documentos automáticamente.

```JS
db.logs.createIndex(
  { fecha: 1 },
  { expireAfterSeconds: 3600 }
)
```

Ideal para:

* Logs
* Tokens
* Sesiones temporales

Concepto interesante: limpieza automática sin cron externo.

### Sparse Index

Un sparse index es un índice que solo incluye documentos que contienen el campo indexado.

Esto puede parecer un detalle menor, pero en términos de arquitectura y rendimiento puede marcar una diferencia significativa.

Conceptualmente, cuando creamos un índice normal sobre un campo opcional, MongoDB indexa también los documentos donde el campo no existe, tratándolo como null. En cambio, el sparse index omite completamente esos documentos.

Ejemplo práctico:

Imaginemos una colección cursos donde solo algunos cursos tienen el campo fechaCertificacion.

Creamos un índice normal:

```JS
db.cursos.createIndex({ fechaCertificacion: 1 })
```

Ahora todos los documentos serán considerados en el índice, incluso los que no tienen el campo.

Si creamos:

```JS
db.cursos.createIndex({ fechaCertificacion: 1 }, { sparse: true })
```

El índice solo incluirá documentos que realmente tengan fechaCertificacion.

¿Qué implica esto?

1. El índice es más pequeño.
2. Las consultas sobre ese campo pueden ser más rápidas.
3. Se reduce el consumo de memoria.

### Text Index

Cuando trabajamos con datos estructurados (números, fechas, estados), los índices tradicionales funcionan perfectamente.

Pero cuando necesitamos buscar texto libre —descripciones, comentarios, títulos, contenido— el problema cambia radicalmente.

Buscar texto no es lo mismo que buscar igualdad exacta.

Aquí entra el Text Index.

Un text index permite realizar búsquedas por palabras dentro de uno o varios campos de tipo string.

Internamente MongoDB:

* Tokeniza el texto.
* Elimina stop words (según idioma).
* Normaliza palabras.
* Construye un índice invertido (similar al modelo básico de motores de búsqueda).

Creación:

Supongamos una colección cursos con:

```JS
{
  nombre: "MongoDB avanzado",
  descripcion: "Curso completo de modelado y optimización"
}
```

Creamos el índice:

```JS
db.cursos.createIndex({ descripcion: "text" })
```

Si queremos incluir múltiples campos:

```JS
db.cursos.createIndex({
  nombre: "text",
  descripcion: "text"
})
```

Importante:
Solo puede existir un text index por colección.
Pero ese índice puede incluir múltiples campos.

Consulta básica

```JS
db.cursos.find({
  $text: { $search: "optimización modelado" }
})
```

MongoDB buscará documentos que contengan esas palabras.

Podemos proyectar el score de relevancia:

```JS
db.cursos.find(
  { $text: { $search: "MongoDB avanzado" } },
  { score: { $meta: "textScore" } }
).sort({ score: { $meta: "textScore" } })
```

Aquí aparece un concepto muy interesante:

MongoDB asigna un peso según coincidencia y frecuencia.

Podemos asignar mayor importancia a un campo:

```JS
db.cursos.createIndex(
  {
    nombre: "text",
    descripcion: "text"
  },
  {
    weights: {
      nombre: 5,
      descripcion: 1
    }
  }
)
```

Esto significa que coincidencias en nombre valen más que en descripcion.

Limitaciones importantes

1. No es un motor de búsqueda completo como Elasticsearch.
2. No soporta búsquedas por rango.
3. No es ideal para análisis semántico complejo.
4. Solo un text index por colección.

Cuándo usarlo

* Búsqueda simple en aplicaciones pequeñas o medianas.
* Filtros básicos tipo “buscar cursos que contengan X”.
* Sistemas donde no se justifica integrar un motor externo.

Cuándo no usarlo

* Sistemas con alta demanda de búsqueda compleja.
* Requerimientos avanzados de stemming, sinónimos, análisis lingüístico profundo.
  

### Hashed Index

El hashed index transforma el valor del campo mediante una función hash interna y luego indexa ese hash.

Ejemplo:

```JS
db.usuarios.createIndex({ usuarioId: "hashed" })
```

El objetivo principal del hashed index no es mejorar búsquedas por rango.

De hecho, no sirve para rangos.

Su propósito real es distribución uniforme.

En sistemas grandes, especialmente cuando se usa sharding, necesitamos que los datos se distribuyan de manera equilibrada entre nodos.

Si usamos como shard key un campo secuencial como fecha o un contador incremental, generamos un hotspot: todos los datos nuevos se insertan en el mismo shard.

En cambio, al usar un hashed index como shard key:

* El hash distribuye valores pseudoaleatoriamente.
* Se reduce concentración en un solo nodo.
* Se mejora paralelismo.

Limitaciones importantes:

* No sirve para consultas por rango.
* No mantiene orden lógico.
* Es ideal para igualdad exacta (field = value).

En términos arquitectónicos:

Hashed es una herramienta de distribución, no de optimización de consulta compleja.

