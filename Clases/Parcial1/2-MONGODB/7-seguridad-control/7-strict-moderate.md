# Modos de validación: strict y moderate

MongoDB permite controlar el comportamiento de la validación mediante diferentes niveles de estricticidad.

Los modos principales son:

* strict
  * Rechaza cualquier documento que no cumpla el esquema
  * Aplica tanto a inserciones como a actualizaciones
* moderate
  * Solo valida documentos nuevos o modificados
  * Permite que documentos antiguos permanezcan aunque no cumplan el esquema

Configuración del nivel de validación:

```JS
db.runCommand({
  collMod: "cursos",
  validationLevel: "strict"
})
```

Elección recomendada según contexto:

| Escenario                       | Nivel recomendado     |
| --------------------------------- | ----------------------- |
| Proyecto nuevo                  | strict                |
| Migración de sistema existente | moderate              |
| Datos históricos heterogéneos | moderate inicialmente |

