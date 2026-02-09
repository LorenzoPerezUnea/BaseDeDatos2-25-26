Aquí tienes la resolución de los ejercicios basada en los factores de selección analizados:

### Ejercicio 1: Matrículas y notas universitarias
*   **Elección:** **SQL (Relacional)**.
*   **Por qué:** Requiere **consistencia fuerte** y transacciones ACID para asegurar que las notas y pagos sean exactos y seguros.
*   **Por qué no los otros:** Las NoSQL suelen priorizar la disponibilidad sobre la consistencia (BASE), lo que podría generar errores en datos críticos como actas de notas.

### Ejercicio 2: Sesiones y preferencias de app móvil
*   **Elección:** **Clave–Valor**.
*   **Por qué:** Ofrece **latencia mínima** (menos de 5ms) y soporte nativo para **TTL** (caducidad automática), ideal para datos temporales y simples.
*   **Por qué no los otros:** SQL o Documental añaden una carga innecesaria para datos que no requieren consultas complejas ni relaciones.

### Ejercicio 3: Sensores industriales y análisis masivo
*   **Elección:** **Columnar**.
*   **Por qué:** Está diseñada para **agregaciones** (resúmenes) sobre miles de millones de registros y escala masivamente en lecturas analíticas.
*   **Por qué no los otros:** SQL colapsa con tal volumen; Clave-Valor y Grafos no permiten realizar promedios o sumas masivas eficientemente.

### Ejercicio 4: CMS con artículos de estructura variable
*   **Elección:** **Documental**.
*   **Por qué:** Permite **esquemas flexibles** donde cada artículo puede tener campos distintos sin necesidad de migraciones de base de datos.
*   **Por qué no los otros:** SQL es demasiado rígido; Columnar está pensado para datos homogéneos, no para contenido textual variado.

### Ejercicio 5: Transferencias bancarias
*   **Elección:** **SQL (Relacional)**.
*   **Por qué:** La **integridad transaccional** es innegociable; garantiza que el dinero nunca desaparezca durante una transferencia.
*   **Por qué no los otros:** La consistencia eventual de la mayoría de las NoSQL podría permitir que una cuenta se descuente sin que la otra reciba el abono simultáneamente.

### Ejercicio 6: Detección de fraude en red social
*   **Elección:** **Grafos**.
*   **Por qué:** Excelente para encontrar **relaciones indirectas** y caminos entre perfiles, mensajes y dispositivos en tiempo real.
*   **Por qué no los otros:** En SQL o Documental, consultar relaciones de segundo o tercer nivel requiere procesos (joins) extremadamente lentos y complejos.

### Ejercicio 7: Buscador semántico de documentos
*   **Elección:** **Vectorial**.
*   **Por qué:** Permite encontrar información por **similitud de significado** (embeddings) en lugar de coincidencia exacta de palabras.
*   **Por qué no los otros:** Las bases de datos tradicionales solo buscan términos literales y no entienden el contexto semántico de una consulta.

### Ejercicio 8: Gestión de empleados y jerarquías simples
*   **Elección:** **SQL (Relacional)**.
*   **Por qué:** Los datos son **estructurados, estables** y de volumen moderado; es el escenario donde SQL es más eficiente y maduro.
*   **Por qué no los otros:** No hay necesidad de la escalabilidad de una Columnar, la flexibilidad de una Documental o la complejidad de una de Grafos.