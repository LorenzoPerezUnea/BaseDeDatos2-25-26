# Problemas reales cuando las relaciones crecen

Ahora vamos a hacer preguntas que suelen aparecer en sistemas reales:

* ¿Quiénes son los amigos de los amigos de Ana?
* ¿Qué usuarios tienen más conexiones en común con otro usuario?
* ¿Qué camino conecta a dos personas dentro de la red?

En un modelo relacional, estas preguntas se resuelven usando joins. El problema es que, a medida que aumenta la profundidad de las relaciones, las consultas se vuelven cada vez más complejas.

Ejemplo sencillo en SQL:

```sql
SELECT u2.name
FROM users u1
JOIN friends f1 ON u1.id = f1.user_id
JOIN users u2 ON f1.friend_id = u2.id
WHERE u1.name = 'Ana';
```

Este ejemplo solo recorre un nivel. Si quisieras recorrer dos o tres niveles, la consulta crecería rápidamente en complejidad.

Aquí aparece una limitación importante: el modelo relacional no está pensado para recorrer relaciones profundas de forma eficiente.

### Ejercicio guiado

Antes de seguir, intenta extender mentalmente la consulta anterior.

Pregunta:

¿Cómo escribirías una consulta para obtener amigos de amigos de amigos?

No hace falta que la escribas completa, pero piensa:

* ¿cuántos joins necesitarías?
* ¿qué tan legible sería?
* ¿qué pasaría si necesitas recorrer 5 niveles?

Este tipo de ejercicio nos ayuda a ver que el problema no es SQL en sí, sino el modelo sobre el que estamos trabajando.

