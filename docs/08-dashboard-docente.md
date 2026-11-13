# 8. Dashboard docente: métricas y gráficas

El dashboard responde en una sola pantalla las preguntas del docente, con filtros globales en la parte superior. Cada vista se alimenta de los eventos de partida (RF-25).

| Vista | Pregunta que responde | Gráfica | Cálculo |
| --- | --- | --- | --- |
| Indicadores clave | ¿Cuántos hay y qué tan activos están? | 4 tarjetas numéricas | Inscritos; activos en los últimos 7 días; % de avance promedio; puntaje promedio |
| Avance por módulo | ¿Cuántos estudiantes y padres han hecho cada módulo? | Barras horizontales apiladas (completado / en curso / sin iniciar) | Usuarios por estado ÷ inscritos, por módulo y rol |
| Avance por estudiante | ¿Cuánto ha avanzado cada uno? | Tabla con barra de progreso y alerta de inactividad | Módulos completados ÷ asignados; días desde la última partida |
| Dónde se sacan más puntos | ¿En qué módulos y juegos les va mejor? | Barras ordenadas de puntaje promedio por juego | Promedio del mejor puntaje normalizado de 0 a 100 |
| Actividades favoritas | ¿Qué juegos les gustaron más? | Dispersión: veces jugado (x) vs. estrellas promedio (y) | Partidas por juego; promedio de calificación de 1 a 5 |
| Falencias | ¿Qué conceptos no se entienden? | Mapa de calor concepto × grupo + lista de preguntas más falladas | Tasa de error por concepto; alerta si supera el 40 % |
| Actividad en el tiempo | ¿Cuándo juegan y si la actividad cae? | Línea de partidas por día o semana | Conteo de partidas por fecha |
| Padres vs. hijos | ¿Las familias acompañan? | Barras agrupadas: avance de padres vs. estudiantes por grupo | % de avance por rol; familias con ambos activos |

## Filtros globales

Grupo, grado (10.° / 11.°), rol (estudiante / padre), módulo y rango de fechas.

## Alertas automáticas

- Estudiante inactivo más de 7 días.
- Concepto con más del 40 % de error.
- Juego con calificación promedio menor a 2,5 estrellas (candidato a rediseño).
- Módulo vencido con menos del 50 % completado.

## Detalle de estudiante

Historial de partidas, mejor puntaje e intentos por juego, conceptos débiles, insignias y si el padre está vinculado y activo.

## Rendimiento

Las métricas agregadas se precalculan cada hora con el Planificador para que el dashboard cargue en menos de 2 s (RNF-05).
