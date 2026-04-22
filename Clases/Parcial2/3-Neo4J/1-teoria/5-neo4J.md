# Introducción a Neo4j

Para trabajar con grafos vamos a utilizar Neo4j.

Neo4j es una base de datos diseñada específicamente para este modelo. No adapta estructuras relacionales, sino que trabaja directamente con nodos y relaciones.

Algunas ideas importantes que iremos viendo en profundidad:

* utiliza un lenguaje de consulta llamado Cypher
* almacena relaciones de forma directa
* permite visualizar los grafos
* está optimizada para recorridos

Lo importante ahora es entender que estamos ante una herramienta pensada para otro tipo de problemas.

### Preparación del entorno con Docker

Vamos a preparar el entorno para poder trabajar desde ya.

Crea un archivo llamado docker-compose.yml:

```yaml
version: '3.8'

services:
  neo4j:
    image: neo4j:5
    container_name: neo4j_bd2
    restart: always
    ports:
      - "7474:7474"
      - "7687:7687"
    environment:
      - NEO4J_AUTH=neo4j/password123
    volumes:
      - neo4j_data:/data

volumes:
  neo4j_data:
```

Este archivo levanta Neo4j con persistencia de datos y acceso tanto web como por consola.

### Levantando el servicio

Desde la carpeta donde está el archivo, ejecuta:

```bash
docker compose up -d
```

Docker descargará la imagen si es necesario y levantará el contenedor.

Puedes comprobarlo con:

```bash
docker ps
```

Verás el contenedor en ejecución.

### Acceso a la interfaz

Abre el navegador y accede a:

[http://localhost:7474](http://localhost:7474/)

Credenciales iniciales:

```id="1r8hjk"
usuario: neo4j
password: password123
```

En el primer acceso tendrás que cambiar la contraseña. Este paso es obligatorio.

Una vez dentro, verás una interfaz que combina editor de consultas y visualización del grafo. Aquí es donde trabajaremos durante todo el bloque.

