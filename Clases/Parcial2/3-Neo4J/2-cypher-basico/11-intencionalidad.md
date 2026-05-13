# Intencionalidad

### Error típico: consultas demasiado amplias

Si ejecutas esto:

```cypher
MATCH (a)-[r:AMIGO_DE*]->(b)
RETURN a, r, b
```

sin límites, puedes obtener resultados enormes.

Esto no es un fallo, es el comportamiento natural del grafo.

Aprender a limitar es parte del dominio de Cypher.

### Introduciendo intención en consultas

Ahora vamos a construir algo más completo.

Antes de escribir, piensa:

* quiero empezar en una persona
* recorrer varios niveles
* filtrar resultados
* controlar cantidad

Ahora ejecuta:

```cypher
MATCH (a:Persona {nombre: "Luis"})-[r:AMIGO_DE*1..3]->(b)
WHERE b.edad > 25
RETURN a,r,  b
LIMIT 10
```

Ejecuta.

Después modifica:

* cambia el filtro
* cambia el nodo inicial
* elimina el límite

Observa qué pasa en cada caso.

# Ejercicio guiado

Ahora construye tu propia consulta combinando:

* patrón
* filtro
* profundidad
* límite

Puedes partir de:

```cypher
MATCH (a:Persona)-[r:AMIGO_DE*1..3]->(b:Persona)
WHERE a.edad > 25
RETURN a, r, b
LIMIT 10
```

Modifica todo lo que quieras.

Este es el momento más importante de la clase.

No busques hacerlo perfecto.

Busca entender qué cambia cuando cambias la forma.

