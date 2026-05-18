# Examen del segundo parcial

[vinculo](https://github.com/GradoIngenieriaInformatica/ExamenSegundoParcial-BD2-2025-2026)



id:7
MATCH (p:Persona) WHERE nombre='Ana' RETURN p

id: 8
MATCH (p:Persona) RETURN p.nombre

id: 12
MATCH p=(a)-[:AMIGO_DE*]->(b) RETURN length(p)

id:13
MATCH p=(a:Persona)-[:AMIGO_DE*1..3]->(b:Persona) RETURN p

id: 18
MATCH (p:Persona)-[:VIVE_EN]->(c:Ciudad) RETURN c.nombre, count(p)

id: 19
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa) RETURN p.nombre, count(e)

id: 23
MATCH (p1:Persona)-[:TRABAJA_EN]->(e)<-[:TRABAJA_EN]-(p2:Persona) RETURN p1.nombre, p2.nombre

id: 25
MATCH (p)-[:PARTICIPA_EN]->(pr) RETURN pr.nombre, sum(horas)

id: 28
MATCH p=(a:Persona)-[:AMIGO_DE*2..3]->(b:Persona) RETURN nodes(p)

id:33
MATCH (p:Persona) WITH p MATCH (p)-[:VIVE_EN]->(c) RETURN c

id:34
MATCH (p:Persona)-[:VIVE_EN]->(c:Ciudad) RETURN c.nombre

id:39
MATCH (p:Persona)-[:AMIGO_DE]->(a:Persona) RETURN p.nombre, count(a)

id: 42
MATCH (p:Persona)-[:PARTICIPA_EN]->(pr:Proyecto) RETURN p.nombre, count(pr)

id:45
MATCH (p:Persona)-[:PARTICIPA_EN]->(pr:Proyecto) RETURN pr.nombre, count(p)

id: 49
MATCH (p1:Persona)-[:TRABAJA_CON]->(p2:Persona) RETURN p1.nombre, p2.nombre

id: 57
MATCH (p:Persona)-[:USA_TECNOLOGIA]->(t:Tecnologia) RETURN p.nombre, collect(t.nombre)

id: 61
MATCH p=(a)-[:AMIGO_DE*]->(b) RETURN UNWIND nodes(p)

id:68
MATCH (p:Persona)-[:TRABAJA_EN]->(e:Empresa) RETURN e.nombre, count(p)

id: 70
MATCH (p:Persona) RETURN p.nombre ORDER p.nombre

id:72
MATCH (p:Persona)-[:AMIGO_DE]->(a) RETURN p.nombre, count(a)

id: 73
MATCH (p:Persona)-[:AMIGO_DE]->(a) WITH p, count(a) as total WHERE total > 0 RETURN p.nombre, total

id:78
MATCH (p:Persona)-[:TRABAJA_CON]->(o:Persona) RETURN p.nombre

id:85
MATCH (p:Persona)-[:VIVE_EN]->(c:Ciudad) RETURN c.nombre

id:98
MATCH (p:Persona)-[:TRABAJA_EN]->(e)-[:VIVE_EN]->(c) RETURN p,e,c
