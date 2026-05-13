# Comparando los modelos con consultas

Vamos a hacer la misma pregunta en distintos modelos.

Pregunta:

personas que trabajan en proyectos de una empresa

Modelo simple:

```cypher
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa {nombre: "SocialCorp"})
RETURN p
```

Modelo con proyecto intermedio:

```cypher
MATCH (p:Persona)-[par:PARTICIPA_EN]->(pr:Proyecto)-[per:PERTENECE_A]->(e:Empresa {nombre: "SocialCorp"})
RETURN p, par, pr, per, e
```

Ambos funcionan.

Pero el segundo es más expresivo.

### Error típico 1: meter todo como propiedades

Muchos alumnos hacen esto:

```cypher
CREATE (p:Persona {
  nombre: "Sonia",
  empresa: "TechCorp",
  proyecto: "Apollo"
})
```

Esto parece simple.

Pero rompe completamente el modelo de grafo.

Problemas:

* no puedes conectar entidades
* no puedes recorrer
* no puedes analizar relaciones

Esto es volver a una base de datos plana.

### Error típico 2: convertir todo en nodos

El extremo opuesto:

```cypher
CREATE (n1:Nombre {valor: "Sonia"})
CREATE (n2:Empresa {valor: "TechCorp"})
CREATE (n3:Proyecto {valor: "Apollo"})
```

Esto genera un grafo artificial.

Demasiados nodos sin significado real.

