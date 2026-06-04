# Encapsulación, reutilización y preparación

### Objetivo operativo

Convertir el sistema actual en una herramienta reutilizable, extensible y preparada para ser usada directamente en el taller.

Hasta ahora el sistema funciona como conjunto de funciones sueltas.
A partir de aquí se transforma en un componente organizado que permite:

* reutilización
* extensión
* modificación controlada

### Problema actual

El sistema está fragmentado:

* funciones separadas
* variables globales (base, index)
* reconstrucción manual

Esto dificulta:

* mantener el sistema
* ampliarlo
* reutilizarlo en otros contextos

### Encapsulación en una clase

```python
class BuscadorSemantico:

    def __init__(self, base):
        self.base = base
        self.index, self.vectores = construir_indice(base)

    def buscar(self, query, k=3):
        return buscar_con_score(query, self.base, self.index, k)

    def agregar(self, texto):
        self.base.append(texto)
        self.index, self.vectores = construir_indice(self.base)
```

### Justificación

Se encapsula:

* datos (base)
* índice (FAISS)
* comportamiento (búsqueda)

Esto permite trabajar con una única entidad coherente.

### Propiedad importante

Cada instancia del sistema:

* tiene su propio espacio vectorial
* tiene su propia base de datos
* es independiente de otras

### Uso inicial

```python
sistema = BuscadorSemantico(base)

print(sistema.buscar("animal"))
```

### Qué cambia respecto a antes

Antes:

* había que gestionar variables externas

Ahora:

* todo está contenido en el objeto
  

