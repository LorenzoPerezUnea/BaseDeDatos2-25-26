# Buenas prácticas

* Indexar campos usados en:
  * filtros frecuentes
  * joins (lookup) - Se explicará posteriormente
  * ordenamientos
* Analizar siempre con explain()
* Medir antes y después
* Mantener número razonable de índices
* Diseñar índices compuestos basados en consultas reales, no hipotéticas
* Usar índices parciales cuando sea posible
* Documentar estrategia de indexación

