# Antipatrones comunes en diseño documental

Entender los errores evita rediseños costosos.

### Sobre-normalización

Intentar replicar modelo relacional:

* Demasiadas colecciones pequeñas.
* Dependencia constante de \$lookup.
* Modelo fragmentado.

Consecuencia:

* Aumento de latencia.
* Mayor consumo de CPU.
* Complejidad innecesaria.

MongoDB no fue optimizado para joins intensivos como un RDBMS.

Si cada consulta requiere 3 \$lookup, el diseño probablemente es incorrecto.

### Documentos sin control de crecimiento

Arrays que crecen sin límite:

```JS
{
  usuario: "Carlos",
  logs: [ ... 50000 registros ... ]
}
```

Problemas:

* Reubicación constante en disco.
* Fragmentación.
* Riesgo de alcanzar límite de 16MB.
* Actualizaciones cada vez más costosas.

Solución:

* Bucket pattern.
* Colección separada.
* TTL.
* Particionamiento lógico.

### Índices innecesarios

Crear índices en todos los campos "por si acaso".

Impacto técnico real:

* Cada insert debe actualizar todos los índices.
* Escrituras más lentas.
* Mayor uso de RAM.
* Mayor uso de disco.
* Rebalanceo más frecuente en sharding.

Regla profesional:

Cada índice debe justificarse por una consulta real medida con explain().

### Uso incorrecto de shard key

Elegir campo monotónico:

```JS
{ fecha: 1 }
```

Genera:

* Hotspot.
* Shard sobrecargado.
* Baja escalabilidad real.

Este error puede obligar a migraciones complejas.

### No medir antes de optimizar

* Agregar índices sin medir.
* Activar sharding sin análisis de carga.
* Optimización sin métricas es especulación.

