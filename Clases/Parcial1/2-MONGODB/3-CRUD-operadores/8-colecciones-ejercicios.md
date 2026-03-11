# Colección: cursos (10 documentos)

## Instrucciones

* Dar de baja al mongodb con el comando:

```Bash
docker compose down
```

* Agregar al docker-compose.yml el siguiente servicio después del mongo express.

```YAML
mongosh:
  image: mongo:7
  container_name: mongosh_docencia
  depends_on:
    - mongodb_docencia
  entrypoint: ["sleep", "infinity"]
```

* Ejecutar en el mismo direcciotrio el siguiente comando

```Bash
docker exec -it mongosh_docencia mongosh mongodb://admin:admin123@mongodb_docencia:27017
```

* Crear una BD para el taller.: con "use".
* Crea la coleccion necesaria con

```js
db.createCollection("cursos")
```

* Agregar las siguientes colecciones a la base de datos creada.

```js
db.cursos.insertMany([
{
  nombre: "Bases de Datos",
  profesor: "Dr. López",
  creditos: 4,
  nivel: "Avanzado",
  estudiantes: ["Ana", "Carlos", "Lucía"],
  activo: true
},
{
  nombre: "Programación Web",
  profesor: "Ing. Torres",
  creditos: 3,
  nivel: "Intermedio",
  estudiantes: ["Pedro", "María"],
  activo: false
},
{
  nombre: "Inteligencia Artificial",
  profesor: "Dra. Ruiz",
  creditos: 5,
  nivel: "Avanzado",
  estudiantes: ["Ana", "Miguel"],
  activo: true
},
{
  nombre: "Minería de Datos",
  profesor: "Dr. Ramírez",
  creditos: 3,
  nivel: "Avanzado",
  estudiantes: ["Lucía", "Andrés"],
  activo: true
},
{
  nombre: "Algoritmos",
  profesor: "Ing. Navarro",
  creditos: 2,
  nivel: "Básico",
  estudiantes: ["Sofía", "Daniel"],
  activo: true
},
{
  nombre: "Estructuras de Datos",
  profesor: "Dr. Campos",
  creditos: 3,
  nivel: "Intermedio",
  estudiantes: ["Carlos", "Elena"],
  activo: true
},
{
  nombre: "Sistemas Operativos",
  profesor: "Dra. Herrera",
  creditos: 4,
  nivel: "Avanzado",
  estudiantes: ["Miguel", "Laura"],
  activo: false
},
{
  nombre: "Redes",
  profesor: "Ing. Castillo",
  creditos: 3,
  nivel: "Intermedio",
  estudiantes: ["Pedro", "Ana"],
  activo: true
},
{
  nombre: "Ciberseguridad",
  profesor: "Dr. Morales",
  creditos: 4,
  nivel: "Avanzado",
  estudiantes: ["Andrés", "Lucía"],
  activo: true
},
{
  nombre: "Matemática Discreta",
  profesor: "Dra. Vega",
  creditos: 2,
  nivel: "Básico",
  estudiantes: ["Daniel", "Sofía"],
  activo: true
}
])
```

### Colección: pedidos (5 documentos)

```js
db.pedidos.insertMany([
{
  cliente: {
    nombre: "Ana Pérez",
    ciudad: "Madrid"
  },
  fecha: "2026-02-10",
  productos: [
    { nombre: "Laptop", precio: 900 },
    { nombre: "Mouse", precio: 25 }
  ],
  total: 925
},
{
  cliente: {
    nombre: "Carlos Gómez",
    ciudad: "Sevilla"
  },
  fecha: "2026-02-11",
  productos: [
    { nombre: "Monitor", precio: 200 },
    { nombre: "Teclado", precio: 50 }
  ],
  total: 250
},
{
  cliente: {
    nombre: "Lucía Martínez",
    ciudad: "Valencia"
  },
  fecha: "2026-02-12",
  productos: [
    { nombre: "Tablet", precio: 300 }
  ],
  total: 300
},
{
  cliente: {
    nombre: "Miguel Torres",
    ciudad: "Madrid"
  },
  fecha: "2026-02-13",
  productos: [
    { nombre: "Laptop", precio: 850 }
  ],
  total: 850
},
{
  cliente: {
    nombre: "Sofía Ramírez",
    ciudad: "Bilbao"
  },
  fecha: "2026-02-14",
  productos: [
    { nombre: "Impresora", precio: 150 }
  ],
  total: 150
}
])
```

### Colección: accesos (5 documentos)

```js
db.accesos.insertMany([
{
  usuario: "ana",
  fecha: "2026-02-18",
  contador: 3
},
{
  usuario: "carlos",
  fecha: "2026-02-18",
  contador: 2
},
{
  usuario: "lucia",
  fecha: "2026-02-18",
  contador: 1
},
{
  usuario: "miguel",
  fecha: "2026-02-18",
  contador: 4
},
{
  usuario: "ana",
  fecha: "2026-02-17",
  contador: 5
}
])
```

