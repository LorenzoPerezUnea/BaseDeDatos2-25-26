# Coste de los índices

No son gratuitos:

* Consumen espacio
* Aumentan tiempo de inserción
* Aumentan tiempo de actualización

Diagrama de impacto:

```mermaid
flowchart TD
    InsertarDocumento --> ActualizarIndice1
    InsertarDocumento --> ActualizarIndice2
    InsertarDocumento --> ActualizarIndiceN
```

