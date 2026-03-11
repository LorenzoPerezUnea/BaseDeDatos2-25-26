# Referencias

Consiste en almacenar documentos separados y relacionarlos mediante identificadores.

```mermaid
flowchart LR
Pedido --> ClienteID
Pedido --> ProductoID1
Pedido --> ProductoID2
ClienteID --> Cliente
ProductoID1 --> Producto
ProductoID2 --> Producto
```

Ventajas:

- Evita duplicación
- Escalable para grandes volúmenes
- Mejor cuando los datos cambian frecuentemente

Limitaciones:

- Requiere consultas adicionales
- Mayor complejidad
- Posible pérdida de rendimiento en lectura

### Payloads de ejemplo

* [Pedido](json/2-pedido.json)
* [Cliente](json/3-cliente.json)

