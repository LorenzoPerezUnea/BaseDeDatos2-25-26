# Índices compuestos avanzados y orden estratégico

Ya vimos que el orden importa.

Pero ahora profundizamos.

Índice:

```JS
{ nivel: 1, creditos: 1, modalidad: 1 }
```

Regla:

MongoDB puede usar:

* nivel
* nivel + creditos
* nivel + creditos + modalidad

Pero NO puede usar eficientemente:

* creditos solo
* modalidad solo

Esto se llama la regla del prefijo.

### Diseño estratégico

Antes de crear un índice compuesto debemos preguntarnos:

* ¿Cuál es el patrón de consulta más frecuente?
* ¿Cuál es el campo más selectivo?
* ¿Cuál es el campo usado para ordenamiento?

El índice debe reflejar el patrón real, no uno hipotético.

### Ejemplo profesional

Consulta frecuente:

```JS
find({ modalidad: "online", nivel: "avanzado" }).sort({ creditos: -1 })
```

Índice ideal:

```JS
{ modalidad: 1, nivel: 1, creditos: -1 }
```

El orden refleja:

Filtro → Filtro → Orden

