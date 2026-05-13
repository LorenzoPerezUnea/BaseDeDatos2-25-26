# Cambio de paradigma: de coincidencia exacta a similitud

Hasta ahora, todos los sistemas que han utilizado funcionan bajo una lógica muy clara:

si algo no coincide exactamente → no existe para el sistema

En SQL:

```python
# conceptual
SELECT * FROM productos WHERE nombre = "cafe"
```

En grafos:

```python
# conceptual
MATCH (p:Producto {nombre: "cafe"})
```

Esto funciona perfectamente para datos estructurados.

Pero ahora planteamos otro tipo de problema:

Buscar:
"café barato"

Y esperar resultados como:
"bebida económica"
"espresso low cost"

Aquí aparece un problema nuevo:
no hay coincidencia exacta, pero sí hay relación de significado.

Ese es el problema que resuelven las bases de datos vectoriales.

### Entorno de trabajo

```yml
version: "3.9"

services:
  vector-db-class:
    image: python:3.11-slim
    ports:
      - "8888:8888"
    volumes:
      - ./notebooks:/app
    working_dir: /app
    command: >
      bash -c "
      pip install --no-cache-dir numpy notebook &&
      jupyter notebook
      --ip=0.0.0.0
      --port=8888
      --no-browser
      --allow-root
      --NotebookApp.token=''
      --NotebookApp.password=''
      "
```

