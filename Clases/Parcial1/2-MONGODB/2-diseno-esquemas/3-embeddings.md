# Embedding

Consiste en incluir datos relacionados dentro del mismo documento.

[Ejemplo conceptual:](json/1-embeddings.json)

Características:

- Documento autocontenido
- Lectura completa en una sola operación
- Ideal cuando los datos siempre se consultan juntos

Ventajas:

- Lectura rápida de entidad completa
- No requiere joins
- Modelo simple

Limitaciones:

- Posible duplicación
- Crecimiento excesivo del documento

### Diagrama JSON jerárquico

```mermaid
graph TD
    Usuario
    Usuario --> Nombre
    Usuario --> Edad
    Usuario --> Direccion
    Direccion --> Ciudad
    Direccion --> Pais
    Usuario --> Roles
    Roles --> Rol1
    Roles --> Rol2
```

### Diagrama tabular plano (relacional)

```mermaid
graph LR
    TablaUsuarios --> Fila1
    Fila1 --> Columna1
    Fila1 --> Columna2
    Fila1 --> Columna3
```

