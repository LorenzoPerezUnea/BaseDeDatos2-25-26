# Identificación de anti-patrones

No indexar:

* Campos con baja cardinalidad (ej: activo true/false)
* Campos que casi nunca se consultan
* Colecciones pequeñas

## Indexar todo

Cada índice:

* Consume RAM
* Ralentiza inserts
* Ralentiza updates

No se indexa “por si acaso”.

## Índices no utilizados

Crear índice sin que ninguna consulta lo use.

Siempre verificar con:

```js
explain()
```

## Índices con bajo cardinalidad

Ejemplo:

```js
{ genero: "M" }
{ genero: "F" }
```

Solo 2 valores.

No mejora mucho.

## Índices desordenados respecto a la consulta

Consulta:

```js
find({ a: 1 }).sort({ b: 1 })
```

Índice incorrecto:

```js
{ b: 1, a: 1 }
```

Orden importa.

