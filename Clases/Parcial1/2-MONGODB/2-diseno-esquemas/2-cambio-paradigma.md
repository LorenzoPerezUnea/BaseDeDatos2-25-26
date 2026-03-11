# Cambio de paradigma respecto a SQL

En bases relacionales el diseño busca:

- Normalización
- Eliminación de redundancia
- Integridad referencial estricta

```mermaid
flowchart LR
    Cliente -->|FK| Pedido
    Pedido -->|FK| DetallePedido
    DetallePedido -->|FK| Producto
```

En bases documentales el diseño busca:

- Optimizar lecturas reales
- Reducir consultas múltiples
- Modelar según cómo la aplicación usa los datos

La decisión afecta:

- Rendimiento
- Consistencia
- Escalabilidad
- Complejidad de consultas
  
  La pregunta ya no es “¿cómo normalizo?”
  La pregunta es “¿cómo se accede a los datos en la práctica?”
  
 ### Paradigma Relacional
  
  ```mermaid
  flowchart
    SQL --> Normalizacion
    SQL --> IntegridadReferencial
    SQL --> JOINs
  ```

### Paradigma Documental

```mermaid
flowchart

MongoDB --> Documentos
MongoDB --> Embedding
MongoDB --> PatronDeAcceso
```

### Flujo de consulta en BD relacional

```mermaid
sequenceDiagram
  participant App
  participant DB

  App->>DB: SELECT * FROM pedido
  App->>DB: JOIN cliente
  App->>DB: JOIN detalle
  App->>DB: JOIN producto
  DB-->>App: Resultado combinado
```

### Flujo de consulta en BD documental

```mermaid
sequenceDiagram
  participant App
  participant MongoDB

  App->>MongoDB: find({pedido_id:1001})
  MongoDB-->>App: Documento completo
```

