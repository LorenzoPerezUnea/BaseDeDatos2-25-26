# Estrategias de escalabilidad

Cuando el sistema crece, el problema deja de ser la consulta puntual y pasa a ser la arquitectura.

Cuando hablamos de escalabilidad en MongoDB debemos distinguir:

Escalabilidad vertical:

* Más CPU
* Más RAM
* Mejor disco

Escalabilidad horizontal:

* Más nodos
* Sharding
* Distribución

MongoDB está diseñado para escalar horizontalmente.

### Sharding — Concepto básico

Sharding distribuye datos entre múltiples nodos.

Clave fundamental:

Shard Key.

La elección de la shard key es crítica porque:

* Determina distribución
* Impacta rendimiento
* No es trivial cambiarla

La shard key determina:

* Cómo se distribuyen los datos.
* Cómo se enrutan las consultas.
* Cómo se balancea la carga.

### Características de una buena shard key:

Alta cardinalidad:
Muchos valores distintos.

Buena distribución:
Evita concentraciones.

Uso frecuente en consultas:
Permite targeted queries en lugar de scatter-gather.

Error común:

Elegir un campo de baja cardinalidad como estado: "activo" / "inactivo".

### Ejemplo conceptual

Shard key mal elegida:

```JS
{ fecha: 1 }
```

Error común:

Elegir un campo de baja cardinalidad como estado: "activo" / "inactivo".

Resultado:
Solo dos shards realmente utilizados.

Error más peligroso:

Elegir un campo monotónico (como fecha creciente).

Resultado:
Todos los inserts recientes van al mismo shard → hotspot.

harding no es solo “dividir datos”.
Es un sistema de particionamiento horizontal automático.

### Objetivo

Permitir que una colección enorme se distribuya entre múltiples servidores (shards).

Arquitectura básica

Un cluster sharded tiene:

1. Shards (nodos que almacenan datos).
2. Config servers (guardan metadata).
3. Mongos (router de consultas).

### Flujo simplificado

Cliente → mongos → shard correspondiente → respuesta

El componente crítico es la shard key.

¿Cómo funciona la shard key?

Cuando insertamos un documento, MongoDB:

1. Evalúa el valor del campo shard key.
2. Determina en qué rango o chunk cae.
3. Lo envía al shard correspondiente.

### Ejemplo práctico conceptual

Supongamos colección pedidos:

```JS
{
  _id: 1,
  clienteId: 1001,
  fecha: ISODate("2026-02-26"),
  total: 200
}
```

Activamos sharding:

```JS
sh.enableSharding("tienda")
```

Seleccionamos shard key:

```JS
sh.shardCollection("tienda.pedidos", { clienteId: 1 })
```

Ahora MongoDB dividirá los datos en rangos de clienteId.

Ejemplo de distribución:

Shard 1: clienteId 1–1000
Shard 2: clienteId 1001–2000
Shard 3: clienteId 2001–3000

¿Qué ocurre en consulta?

Consulta:

```JS
db.pedidos.find({ clienteId: 1500 })
```

MongoDB puede enrutar directamente al Shard 2.

Esto se llama targeted query.

Consulta sin shard key:

```JS
db.pedidos.find({ total: { $gt: 100 } })
```

MongoDB debe consultar todos los shards.

Esto se llama scatter-gather.

### Problema de hotspot

Si usamos como shard key:

```JS
{ fecha: 1 }
```

Y todos los pedidos nuevos tienen fecha actual,
todos los inserts irán al shard con el rango más alto.

Resultado:
Un shard sobrecargado.
Otros ociosos.

Solución posible:

Usar hashed shard key:

```JS
sh.shardCollection("tienda.pedidos", { clienteId: "hashed" })
```

Ahora los datos se distribuyen pseudoaleatoriamente.

Beneficio:
Carga equilibrada.

Desventaja:
Consultas por rango de clienteId no serán eficientes.

### Balanceo automático

MongoDB divide datos en chunks (por ejemplo 64MB).
Cuando un chunk crece demasiado, se divide.
Si un shard tiene demasiados chunks, el balancer mueve algunos a otros shards.

Este proceso es automático.

### Ejercicio conceptual

Dado:

Sistema de logs:

* 5 millones de eventos diarios.
* Consultas frecuentes por usuarioId.
* Reportes ocasionales por fecha.

Preguntas para discusión:

1. ¿Shard key por fecha?
2. ¿Shard key por usuarioId?
3. ¿Combinación?
4. ¿Hashed?

Respuesta esperada:
Probablemente usuarioId o hashed(usuarioId) si el volumen es extremo.

Cuando un sistema alcanza millones de documentos, la diferencia entre diseño correcto e incorrecto deja de ser teórica y se vuelve financiera.

Si deseas, podemos ahora preparar:

