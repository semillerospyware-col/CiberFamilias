# 4. Catálogo de mecánicas de juego

Todos los juegos son plantillas reutilizables. El docente solo carga el contenido (palabras, preguntas, pares) y el motor genera el juego, lo puntúa y envía los eventos a la analítica.

| Código | Mecánica | Cómo se juega | Contenido que carga el docente | Cómo puntúa |
| --- | --- | --- | --- | --- |
| J01 | Crucigrama | Completar palabras cruzadas a partir de pistas | Lista de palabra + pista | 10 pts por palabra; −2 por pista extra |
| J02 | Sopa de letras | Encontrar términos ocultos en una cuadrícula, contra reloj | Lista de términos + tamaño de cuadrícula | 10 pts por término + bono por tiempo |
| J03 | Saltar la hoja | Runner: el personaje salta obstáculos (ataques, virus) y recoge escudos que abren preguntas | Banco de preguntas + tipo de obstáculo | Distancia + respuestas correctas |
| J04 | Verdadero o falso | Deslizar la tarjeta a izquierda o derecha | Afirmaciones + respuesta + explicación | 10 pts por acierto; racha ×1,5 |
| J05 | Emparejar parejas | Memoria: voltear cartas concepto ↔ definición | Pares | Pares hallados ÷ intentos |
| J06 | Arrastrar y soltar / Clasificar | Llevar elementos a la categoría correcta | Elementos + categorías | % de elementos bien ubicados |
| J07 | Ordenar pasos | Ordenar una secuencia (p. ej. configurar el control parental) | Pasos en el orden correcto | % de posiciones correctas |
| J08 | Ruleta / Trivia contrarreloj | Girar la ruleta y responder opción múltiple con tiempo | Preguntas + opciones | Aciertos + bono de velocidad |
| J09 | Simulador de escenario | Historia ramificada: elegir qué hacer ante un caso real | Nodos de decisión + consecuencia | Puntos por decisión segura |
| J10 | Cazador de phishing | Revisar correos o mensajes simulados y marcar los fraudulentos | Mensajes + señales de alerta | Aciertos; penaliza falsos positivos |

## Reglas comunes a todos los juegos

- Duración objetivo: 2 a 5 minutos por partida.
- Retroalimentación inmediata con la explicación del concepto tras cada error.
- Reintentos ilimitados; se guarda el mejor puntaje y el número de intentos.
- Al terminar, el jugador califica el juego de 1 a 5 estrellas. Esto alimenta la métrica «¿qué actividad gustó más?».
- Cada pregunta está etiquetada con un concepto, para detectar falencias por concepto y no solo por módulo.

## Interfaz común de una plantilla

Cada mecánica es un componente independiente (RNF-12) que implementa el mismo contrato:

| Operación | Descripción |
| --- | --- |
| `cargar(contenido)` | Recibe el contenido configurado por el docente y valida que sea suficiente |
| `emitir(evento)` | Envía `inicio`, `respuesta` (acierto/error + concepto), `abandono` y `fin` |
| `puntuar()` | Devuelve el puntaje normalizado de 0 a 100 y el detalle por pregunta |
