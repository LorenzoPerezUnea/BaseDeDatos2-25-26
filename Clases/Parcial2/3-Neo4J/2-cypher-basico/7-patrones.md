# Patrones

En la primera parte trabajaste con nodos, relaciones y recorridos simples. Ahora vamos a profundizar en algo que ya has usado pero aún no dominas: cómo escribir patrones con precisión.

Vamos a empezar con algo que ya conoces:

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
RETURN a, r, b
```

Ejecuta.

Ahora no mires solo el resultado. Piensa qué estás describiendo exactamente:

* un nodo de tipo Persona
* conectado a otro nodo Persona
* mediante una relación específica

Esto es importante: no estás pidiendo datos, estás definiendo una forma dentro del grafo.

### Introduciendo filtros de forma consciente

Vamos a añadir una condición.

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
WHERE a.edad > 25
RETURN a, r, b
```

Ejecuta.

Ahora cambia el filtro:

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
WHERE b.edad > 30
RETURN a, r, b
```

Detente.

Mismo patrón, distinto resultado.

Esto es algo que muchos alumnos no interiorizan: el patrón define la estructura, el WHERE ajusta el resultado.

### Variación combinada

Ahora combina condiciones:

```cypher
MATCH (a:Persona)-[r:AMIGO_DE]->(b:Persona)
WHERE a.edad > 25 AND b.edad > 30
RETURN a, r, b
```

Ejecuta.

Después cambia AND por OR.

Observa cómo cambia el resultado.

No avances rápido aquí. Este tipo de variaciones construyen intuición.

