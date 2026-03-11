# Buenas prácticas profesionales

### 1. Diseñar pensando en consultas reales

No crear pipelines hipotéticos.
Analizar qué preguntas reales necesita el sistema.

### 2. Usar índices estratégicamente

Especialmente en campos usados en `$match`.

### 3. Proyectar solo lo necesario

Menos datos = menos memoria.

### 4. Evitar pipelines innecesariamente largos

Un pipeline de 15 etapas puede indicar complejidad excesiva.

### 5. Medir siempre

Nunca asumir rendimiento.
Siempre validar con `explain()`.

