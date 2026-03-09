# Modelo mental final

Sin índice:

```mermaid
flowchart TD
    A[Consulta] --> B[Leer todo]
    B --> C[Filtrar]
```

Con índice:

```mermaid
flowchart TD
    A[Consulta] --> B[Ir al índice]
    B --> C[Leer pocos documentos]
```

### Conclusión

Los índices no hacen la base “más rápida”.

Hacen las consultas específicas más eficientes.

Pero:

* Penalizan escritura
* Consumen memoria
* Requieren diseño estratégico

En sistemas reales, el diseño de índices es una disciplina propia dentro de la arquitectura de datos.

```mermaid
flowchart TD
    A[Consulta] --> B{¿Hay índice adecuado?}
    B -- No --> C[COLLSCAN]
    B -- Sí --> D[IXSCAN]
    D --> E[Menos documentos examinados]
```

