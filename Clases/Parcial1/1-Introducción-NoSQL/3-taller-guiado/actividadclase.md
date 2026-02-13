## Ejercicio 1

**Enunciado:**  
Una universidad necesita gestionar matrículas, asignaturas, profesores y actas de notas. Se requiere asegurar consistencia fuerte en las calificaciones y transacciones seguras durante los periodos de matrícula.

**Respuesta:**  
Base de datos Relacional (SQL).

**Justificación:**  
- Relaciones bien definidas entre entidades.  
- Necesidad de consistencia fuerte.  
- Transacciones que deben cumplir ACID.  
- Modelo estructurado y estable.  
- No se requiere escalabilidad horizontal masiva.  

---

## Ejercicio 2

**Enunciado:**  
Una aplicación móvil debe almacenar preferencias de usuario, tokens de sesión y configuraciones temporales. El acceso debe ser inmediato y los datos pueden eliminarse automáticamente tras un tiempo de inactividad.

**Respuesta:**  
Base de datos Clave–Valor (NoSQL).

**Justificación:**  
- Acceso directo por clave.  
- No existen relaciones complejas.  
- Se prioriza velocidad.  
- Datos temporales con expiración automática.  
- No se requieren consultas complejas.  

---

## Ejercicio 3

**Enunciado:**  
Una empresa de análisis recopila millones de registros diarios de sensores industriales y su volumen va en aumento. Los analistas consultan resúmenes por día, planta y tipo de sensor para generar informes históricos.

**Respuesta:**  
Base de datos Columnar (NoSQL).

**Justificación:**  
- Muy alto volumen de datos.  
- Consultas orientadas a agregaciones y estadísticas.  
- Predominio de lecturas analíticas.  
- Interés en patrones globales.  
- Necesidad de escalabilidad horizontal.  

---

## Ejercicio 4

**Enunciado:**  
Un sistema de gestión de contenidos permite que cada artículo tenga campos distintos según su tipo. Algunos incluyen galerías, otros videos, otros solo texto, y el modelo cambia con frecuencia.

**Respuesta:**  
Base de datos Documental (NoSQL).

**Justificación:**  
- Estructura variable entre entidades.  
- Cambios frecuentes en el modelo.  
- Entidades autocontenidas.  
- Consultas flexibles por campos.  
- Evita migraciones constantes de esquema.  

---

## Ejercicio 5

**Enunciado:**  
Un banco necesita registrar transferencias entre cuentas, asegurando que nunca se pierda dinero y que cada operación sea completamente consistente, incluso ante fallos del sistema.

**Respuesta:**  
Base de datos Relacional (SQL).

**Justificación:**  
- Dominio altamente transaccional.  
- Riesgo crítico ante inconsistencias.  
- Necesidad de atomicidad y durabilidad.  
- Modelo claro entre cuentas y movimientos.  
- No se acepta consistencia eventual.  

---

## Ejercicio 6

**Enunciado:**  
Una red social quiere detectar comunidades de usuarios, relaciones indirectas y conexiones sospechosas entre perfiles, mensajes y dispositivos compartidos.

**Respuesta:**  
Base de datos de Grafos (NoSQL).

**Justificación:**  
- El valor está en las relaciones.  
- Consultas basadas en recorridos y caminos.  
- Análisis de conexiones indirectas.  
- Relaciones con significado propio.  
- SQL requeriría múltiples joins complejos.  

---

## Ejercicio 7

**Enunciado:**  
Un buscador interno debe permitir encontrar documentos similares a una descripción escrita por el usuario, aunque no coincidan exactamente las palabras utilizadas.

**Respuesta:**  
Base de datos Vectorial (NoSQL).

**Justificación:**  
- Búsqueda por similitud semántica.  
- Comparación aproximada.  
- Uso de embeddings vectoriales.  
- Integración con modelos de lenguaje.  
- No eficiente con SQL tradicional.  

---

## Ejercicio 8

**Enunciado:**  
Un sistema corporativo gestiona empleados, departamentos y jerarquías simples. El volumen de datos es moderado y las relaciones están bien definidas y son estables en el tiempo.

**Respuesta:**  
Base de datos Relacional (SQL).

**Justificación:**  
- Modelo simple y bien definido.  
- Volumen controlado.  
- Relaciones claras y estables.  
- Consultas estructuradas previsibles.  
- No se justifica la complejidad de NoSQL.  
