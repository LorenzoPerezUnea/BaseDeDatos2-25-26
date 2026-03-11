# \$project — Transformación estructural

Mientras `$group` agrupa, `$project` transforma la forma del documento.

Ejemplo:

```JS
db.cursos.aggregate([
  {
    $project: {
      nombre: 1,
      creditosDobles: { $multiply: ["$creditos", 2] }
    }
  }
])
```

Aquí estamos:

* Seleccionando campos
* Creando campos calculados
* Eliminando campos innecesarios

Esto es muy potente cuando queremos:

* Formatear resultados
* Preparar datos para frontend
* Reducir payload

### Diferencia clave con find()

`find()` solo incluye/excluye campos.

`$project` puede:

* Crear campos
* Renombrar
* Calcular
* Reestructurar

