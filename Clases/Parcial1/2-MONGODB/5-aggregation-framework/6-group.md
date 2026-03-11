# \$group — El núcleo analítico

Aquí comienza la parte verdaderamente transformacional.

Ejemplo:

```JS
db.cursos.aggregate([
  {
    $group: {
      _id: "$nivel",
      totalCursos: { $sum: 1 }
    }
  }
])
```

Vamos a analizarlo cuidadosamente.

* `_id` define la clave de agrupación
* `$sum: 1` cuenta documentos
* El resultado ya no son cursos
* El resultado son agrupaciones

Salida conceptual:

```JS
{ "_id": "básico", "totalCursos": 3 }
{ "_id": "intermedio", "totalCursos": 1 }
{ "_id": "avanzado", "totalCursos": 1 }
```

Observa algo fundamental:

El documento original desaparece.
Ahora estamos trabajando con una estructura nueva.

Esto es procesamiento analítico.

### Acumuladores importantes

### \$sum

Cuenta o suma valores numéricos.

```JS
totalCreditos: { $sum: "$creditos" }
```

### \$avg

Promedio:

```JS
promedio: { $avg: "$creditos" }
```

### \$max / \$min

Permiten encontrar extremos.

```JS
cursos: { $min: "$creditos" }
```

```JS
cursos: { $max: "$creditos" }
```

### \$push

Crea un array con valores agrupados.

```JS
cursos: { $push: "$nombre" }
```

Aquí ya estamos creando estructuras más complejas.

