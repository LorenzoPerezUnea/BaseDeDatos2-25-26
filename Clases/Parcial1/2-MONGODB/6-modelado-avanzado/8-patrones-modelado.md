# Patrones de modelado en MongoDB

En MongoDB el modelado no es una traducción de lo relacional.
Es una decisión estratégica basada en:

* Frecuencia de lectura
* Frecuencia de escritura
* Atomicidad requerida
* Crecimiento esperado
* Tamaño del documento
* Patrón de consulta dominante

El error más común es modelar por intuición estructural en lugar de modelar por comportamiento de acceso.

### Subset Pattern — Optimización por acceso frecuente

El Subset Pattern consiste en almacenar solo una parte relevante de un conjunto grande dentro del documento principal.

Ejemplo real:

Un usuario tiene 10,000 pedidos, pero en la aplicación solo se muestran los últimos 5.

Modelo optimizado:

```JS
{
  _id: 1,
  nombre: "Carlos",
  ultimosPedidos: [
    { pedidoId: 201, total: 300 },
    { pedidoId: 202, total: 150 }
  ]
}
```

El histórico completo está en otra colección.

Impacto técnico:

* Reduce tamaño de documento principal.
* Mejora tiempo de lectura.
* Evita \$lookup frecuente.
* Mantiene documento dentro de límites de memoria.

Riesgo:

* Debe mantenerse sincronizado.
* Requiere lógica de actualización controlada.

Este patrón es ideal cuando el acceso es muy sesgado hacia información reciente.

### Bucket Pattern — Optimización para series temporales

Diseñado para datos que crecen continuamente (logs, sensores, métricas).

En lugar de:

```JS
{ sensorId: 1, fecha: t1, valor: 20 }
{ sensorId: 1, fecha: t2, valor: 21 }
```

Se agrupan:

```JS
{
  sensorId: 1,
  fechaInicio: t1,
  valores: [20, 21, 22, 23]
}
```

Ventajas técnicas:

* Reduce número de documentos.
* Reduce carga en índices.
* Reduce sobrecarga de metadata.
* Mejora rendimiento de lectura agregada.

Consideración crítica:

El tamaño del bucket debe ser controlado.
No debe crecer indefinidamente.

En sistemas de alto volumen, este patrón puede reducir almacenamiento hasta 40–60%.

### Extended Reference Pattern — Equilibrio entre duplicación y consistencia

En lugar de:

```JS
pedido: { clienteId: ObjectId(...) }
```

Se guarda:

```JS
pedido: {
  clienteId: ObjectId(...),
  nombreCliente: "Ana",
  ciudadCliente: "Madrid"
}
```

Esto permite:

* Evitar \$lookup en consultas frecuentes.
* Reducir latencia.
* Mejorar rendimiento en lectura masiva.

Costo:

* Duplicación de datos.
* Necesidad de actualización propagada si cambia el cliente.

Regla profesional:

Duplicar datos cuando el costo de inconsistencia es menor que el costo de consulta repetitiva.

### Computed Pattern — Precalcular para rendimiento

En sistemas de alto tráfico, recalcular agregaciones constantemente es costoso.

Ejemplo:

En lugar de calcular promedio de notas cada vez:

Guardar:

```JS
{
  cursoId: 10,
  promedioNotas: 4.3,
  totalInscripciones: 120
}
```

Se actualiza cuando cambia una nota.

Este patrón es clave en sistemas financieros y dashboards.

