# Evolución controlada del esquema

A lo largo de la vida de una aplicación, los esquemas evolucionan. Nuevos campos aparecen, otros se eliminan y algunos cambian de tipo.

Una estrategia profesional para evolucionar esquemas incluye:

1. Definir la nueva versión del esquema
2. Actualizar la validación de la colección
3. Migrar documentos antiguos
4. Activar validación estricta

Ejemplo de migración simple:

```JS
db.cursos.updateMany(
{ creditos: { $exists: false } },
{ $set: { creditos: 3 } }
)
```

Este tipo de scripts permite adaptar documentos antiguos a nuevas reglas estructurales.

