# Operadores principales

### $set

* Crea o modifica campos
* Puede actuar sobre rutas anidadas

```js
{ $set: { "cliente.telefono": "555-1234" } }
```

### $unset

Elimina un campo completamente.

```js
{ $unset: { telefono: "" } }
```

Uso típico: limpieza de datos obsoletos.

### $inc

* Incrementa valores numéricos.
* Evita condiciones de carrera en contadores.

```js
{ $inc: { visitas: 1 } }
```

```mermaid
sequenceDiagram
    participant U1
    participant U2
    participant DB

    U1->>DB: $inc visitas +1
    DB-->>U1: actualizado
    U2->>DB: $inc visitas +1
    DB-->>U2: actualizado
```

MongoDB garantiza atomicidad a nivel documento.

### Modificación en documentos embebidos

```js
db.pedidos.updateOne(
  { "cliente.nombre": "Ana Pérez" },
  { $set: { "cliente.ciudad": "Barcelona" } }
)
```



