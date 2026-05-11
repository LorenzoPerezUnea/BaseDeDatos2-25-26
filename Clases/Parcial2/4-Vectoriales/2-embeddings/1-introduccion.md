# Diseño del espacio vectorial

### El embedding como decisión de modelado

En esta sesión no se parte de un embedding dado, sino que se construye desde cero. La idea central es que un embedding no es algo fijo, sino una representación que depende de cómo se define el espacio vectorial.

Dos sistemas distintos pueden representar el mismo conjunto de palabras de formas completamente diferentes, y eso cambia directamente los resultados de búsqueda.

Se va a trabajar con un vocabulario pequeño, pero diseñado de forma explícita.

```python
import numpy as np
```



