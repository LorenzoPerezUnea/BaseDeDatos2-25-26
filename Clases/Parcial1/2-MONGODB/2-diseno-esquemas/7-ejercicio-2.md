# EJERCICIO 2 — Pedidos con estructura embebida

### ENUNCIADO

Se desea registrar pedidos de una tienda online.

1. Crear una base de datos: tienda
2. Crear una colección: pedidos
3. Insertar 2 documentos donde cada pedido tenga:

* cliente (objeto embebido con nombre y ciudad)
* fecha
* lista de productos (array de objetos con nombre y precio)
* total

Ejemplo conceptual:

* Un cliente puede tener varios productos en el mismo pedido
* Cada producto debe ser un objeto dentro del array

4. Realizar consultas:

* Buscar pedidos de clientes de una ciudad específica
* Buscar pedidos donde exista un producto con precio mayor a 100
* Buscar pedidos cuyo total sea mayor a 300

### Solución

### jsons de pedidos

* [Pedido 1.](json/7-pedido-1.json)
* [Pedido 2.](json/8-pedido-2.json)
* [Pedido 3.](json/9-pedido-3.json)

### condiciones a ejecutar

* Buscar pedidos de clientes de una ciudad específica: { "cliente.ciudad": "Madrid" }
* Buscar pedidos donde exista un producto con precio mayor a 100: { "productos.precio": { "$gt": 100 } }
* Buscar pedidos cuyo total sea mayor a 300: { "total": { "$gt": 300 } }

