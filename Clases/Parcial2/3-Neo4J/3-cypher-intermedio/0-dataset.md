```cypher
// =========================
// PERSONAS
// =========================

CREATE
(p1:Persona {nombre: "Ana", edad: 25}),
(p2:Persona {nombre: "Luis", edad: 30}),
(p3:Persona {nombre: "Carlos", edad: 28}),
(p4:Persona {nombre: "Marta", edad: 35}),
(p5:Persona {nombre: "Sofia", edad: 27}),
(p6:Persona {nombre: "Diego", edad: 40}),
(p7:Persona {nombre: "Elena", edad: 32}),
(p8:Persona {nombre: "Jorge", edad: 29}),
(p9:Persona {nombre: "Lucia", edad: 31}),
(p10:Persona {nombre: "Pedro", edad: 45})

// =========================
// EMPRESAS
// =========================

CREATE
(e1:Empresa {nombre: "TechCorp", sector: "Tecnologia"}),
(e2:Empresa {nombre: "FinBank", sector: "Finanzas"}),
(e3:Empresa {nombre: "HealthPlus", sector: "Salud"})

// =========================
// PROYECTOS
// =========================

CREATE
(pr1:Proyecto {nombre: "Apollo", presupuesto: 100000}),
(pr2:Proyecto {nombre: "Hermes", presupuesto: 50000}),
(pr3:Proyecto {nombre: "Gaia", presupuesto: 75000})

// =========================
// CIUDADES
// =========================

CREATE
(c1:Ciudad {nombre: "Madrid"}),
(c2:Ciudad {nombre: "Barcelona"}),
(c3:Ciudad {nombre: "Valencia"})

// =========================
// RELACIONES PERSONA-PERSONA
// =========================

CREATE
(p1)-[:AMIGO_DE {desde: 2020, intensidad: 7}]->(p2),
(p2)-[:AMIGO_DE {desde: 2018, intensidad: 9}]->(p3),
(p3)-[:AMIGO_DE {desde: 2019, intensidad: 6}]->(p4),
(p4)-[:AMIGO_DE {desde: 2021, intensidad: 8}]->(p5),
(p5)-[:AMIGO_DE {desde: 2022, intensidad: 5}]->(p1),

(p6)-[:AMIGO_DE {desde: 2015, intensidad: 9}]->(p7),
(p7)-[:AMIGO_DE {desde: 2016, intensidad: 7}]->(p8),
(p8)-[:AMIGO_DE {desde: 2017, intensidad: 6}]->(p9),
(p9)-[:AMIGO_DE {desde: 2018, intensidad: 8}]->(p10),

(p2)-[:AMIGO_DE {desde: 2023, intensidad: 4}]->(p5),
(p3)-[:AMIGO_DE {desde: 2022, intensidad: 7}]->(p7)

// =========================
// RELACIONES LABORALES
// =========================

CREATE
(p1)-[:TRABAJA_EN {desde: 2021, rol: "Developer"}]->(e1),
(p2)-[:TRABAJA_EN {desde: 2019, rol: "Manager"}]->(e1),
(p3)-[:TRABAJA_EN {desde: 2020, rol: "Analyst"}]->(e2),
(p4)-[:TRABAJA_EN {desde: 2018, rol: "HR"}]->(e2),
(p5)-[:TRABAJA_EN {desde: 2022, rol: "Intern"}]->(e1),

(p6)-[:TRABAJA_EN {desde: 2010, rol: "Director"}]->(e3),
(p7)-[:TRABAJA_EN {desde: 2015, rol: "Doctor"}]->(e3),
(p8)-[:TRABAJA_EN {desde: 2021, rol: "Nurse"}]->(e3)

// =========================
// COLABORACIONES
// =========================

CREATE
(p1)-[:TRABAJA_CON {proyecto: "Apollo"}]->(p2),
(p2)-[:TRABAJA_CON {proyecto: "Apollo"}]->(p3),
(p3)-[:TRABAJA_CON {proyecto: "Hermes"}]->(p4),
(p4)-[:TRABAJA_CON {proyecto: "Gaia"}]->(p5),

(p6)-[:TRABAJA_CON {proyecto: "Health"}]->(p7),
(p7)-[:TRABAJA_CON {proyecto: "Health"}]->(p8)

// =========================
// PROYECTOS
// =========================

CREATE
(e1)-[:GESTIONA]->(pr1),
(e2)-[:GESTIONA]->(pr2),
(e3)-[:GESTIONA]->(pr3),

(p1)-[:PARTICIPA_EN]->(pr1),
(p2)-[:PARTICIPA_EN]->(pr1),
(p3)-[:PARTICIPA_EN]->(pr2),
(p4)-[:PARTICIPA_EN]->(pr2),
(p6)-[:PARTICIPA_EN]->(pr3)

// =========================
// UBICACIÓN
// =========================

CREATE
(p1)-[:VIVE_EN]->(c1),
(p2)-[:VIVE_EN]->(c1),
(p3)-[:VIVE_EN]->(c2),
(p4)-[:VIVE_EN]->(c2),
(p5)-[:VIVE_EN]->(c3),

(p6)-[:VIVE_EN]->(c3),
(p7)-[:VIVE_EN]->(c1),
(p8)-[:VIVE_EN]->(c2),
(p9)-[:VIVE_EN]->(c3),
(p10)-[:VIVE_EN]->(c1)
```

