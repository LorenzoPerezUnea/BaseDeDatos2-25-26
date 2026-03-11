# Comparación conceptual con SQL

SQL:

```sql
UPDATE cursos SET creditos = creditos + 1 WHERE nombre = 'BD';
```

MongoDB:

```js
db.cursos.updateOne(
  { nombre: "BD" },
  { $inc: { creditos: 1 } }
)
```

Diferencia fundamental:

* SQL opera sobre tablas normalizadas.
* MongoDB opera sobre documentos completos como unidad estructural.

