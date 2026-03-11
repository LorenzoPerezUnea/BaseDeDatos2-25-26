# Entorno de práctica con Docker

Para trabajar en clase es recomendable levantar MongoDB y una interfaz visual como Mongo Express usando Docker.

### Instrucciones básicas para los estudiantes:

1. Crear un directorio.
2. Guardar el archivo como [docker-compose.yml](docker-compose/docker-compose.yml)
3. Ejecutar:
   docker compose up -d --build
4. Acceder a:
   [http://localhost:8081](http://localhost:8081)

Esto permite:

* Ver bases de datos
* Crear colecciones
* Insertar documentos
* Explorar el modelo documental visualmente

