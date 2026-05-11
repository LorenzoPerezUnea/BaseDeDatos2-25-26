# Construyendo consultas más expresivas

Vamos a combinar varias ideas.

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
MATCH (b)-[:TRABAJA_EN]->(e:Empresa)
WHERE r.intensidad > 6
RETURN a.nombre, b.nombre, e.nombre, r.desde
ORDER BY r.intensidad DESC
```

Ejecuta.

Esto ya parece una consulta de negocio real.

### Ejercicio guiado

Ahora modifica la consulta para:

* filtrar por año
* cambiar orden
* devolver distintas propiedades

Ejemplo base:

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
MATCH (b)-[:VIVE_EN]->(c:Ciudad)
WHERE r.desde > 2020
RETURN a.nombre, c.nombre, r.intensidad
```

Ejecuta, cambia, vuelve a ejecutar.

