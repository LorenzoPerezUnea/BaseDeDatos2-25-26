### Ejercicio 1 – Base de datos relacional (SQL)

* Las entidades mantienen relaciones claras y definidas  
* Se requiere mantener consistencia estricta en todo momento  
* Las transacciones cumplen con las propiedades ACID  
* El esquema de datos es estable y organizado  
* No se necesita escalabilidad horizontal masiva  

### Ejercicio 2 – Base de datos Clave–Valor (NoSQL)

* Acceso inmediato mediante clave única  
* No hay dependencias entre registros  
* La prioridad es la rapidez sobre la complejidad  
* Los datos son efímeros y pueden expirar automáticamente  
* Consultas complejas no son necesarias  

### Ejercicio 3 – Base de datos Columnar (NoSQL)

* Gran cantidad de datos generados diariamente  
* Consultas centradas en agregados y estadísticas  
* Predominan operaciones de lectura analítica  
* Interés en tendencias globales más que en datos individuales  
* Escalabilidad horizontal requerida  

### Ejercicio 4 – Base de datos Documental (NoSQL)

* Cada entidad puede tener un formato distinto  
* El esquema cambia frecuentemente  
* Cada documento es autocontenido por naturaleza  
* Necesidad de búsquedas flexibles según campos  
* Minimiza la necesidad de migraciones de esquema  

### Ejercicio 5 – Base de datos relacional (SQL)

* Dominio con alta frecuencia de transacciones  
* Inconsistencias podrían ser críticas  
* Se requiere atomicidad y durabilidad de operaciones  
* Relaciones claras entre cuentas y movimientos  
* No se acepta consistencia eventual  

### Ejercicio 6 – Base de datos de Grafos (NoSQL)

* El valor se encuentra en las conexiones entre entidades  
* Se investigan relaciones indirectas  
* Consultas basadas en caminos y recorridos  
* Las relaciones tienen importancia propia  
* SQL tradicional necesitaría múltiples joins complejos  

### Ejercicio 7 – Base de datos Vectorial (NoSQL)

* Búsqueda basada en similitud conceptual  
* Comparaciones aproximadas en lugar de exactas  
* Se usan representaciones vectoriales de los datos  
* Compatible con modelos de lenguaje o embeddings  
* SQL tradicional no ofrece solución eficiente  

### Ejercicio 8 – Base de datos relacional (SQL)

* Modelo de datos sencillo y bien estructurado  
* Cantidad de datos manejable  
* Relaciones definidas y estables  
* Consultas previsibles y estructuradas  
* La complejidad de NoSQL no se justifica  
