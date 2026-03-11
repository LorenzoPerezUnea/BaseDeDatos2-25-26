# Observabilidad y monitoreo básico

Un sistema sin observabilidad no es profesional.

MongoDB permite monitoreo en tres niveles:

1. Nivel de consulta
2. Nivel de base de datos
3. Nivel de cluster

### Nivel de Consulta — Explain profundo

Comando clave:

```JS
db.cursos.find({ nivel: "avanzado" }).explain("executionStats")
```

Campos críticos a analizar:

* stage (IXSCAN o COLLSCAN)
* totalDocsExamined
* totalKeysExamined
* executionTimeMillis

Interpretación profesional:

Si totalDocsExamined >> nReturned
El índice no es óptimo.

Si aparece COLLSCAN
Falta índice o índice incorrecto.

### Nivel de Base de Datos — serverStatus

```JS
db.serverStatus()
```

Métricas clave:

* opcounters (lecturas y escrituras)
* connections
* mem
* wiredTiger.cache

Un aumento constante en cache eviction puede indicar presión de memoria.

### Nivel de Índices — Uso real

```JS
db.collection.getIndexes()
```

Pero lo importante es:

Identificar índices no usados.

En entornos productivos se analizan:

* Index usage stats
* Plan cache

Un índice no utilizado es deuda técnica.

### Monitoreo en entornos distribuidos

En sistemas con sharding:

Se debe monitorear:

* Balanceo de chunks
* Distribución por shard
* Latencia por shard
* Throughput por nodo

Una distribución desigual implica mala shard key.

### Cultura de monitoreo continuo

Práctica recomendada:

1. Establecer métricas base.
2. Aplicar cambio.
3. Medir impacto.
4. Revertir si empeora.

La optimización es iterativa.

