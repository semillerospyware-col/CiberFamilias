# 5. Requisitos funcionales

Son 48 requisitos en 7 áreas. Prioridad: **Alta** = imprescindible para la v1, **Media** = deseable en la v1, **Baja** = versiones posteriores.

## 5.1 Autenticación y cuentas

| ID | Requisito | Actor | Prioridad |
| --- | --- | --- | --- |
| RF-01 | El sistema debe permitir registrarse con correo y contraseña o con cuenta Google institucional. | Usuario | Alta |
| RF-02 | El sistema debe permitir unirse a un grupo mediante un código de clase de 7 caracteres generado por el docente. | Estudiante, Padre | Alta |
| RF-03 | El sistema debe permitir iniciar y cerrar sesión, y recuperar la contraseña por correo. | Usuario | Alta |
| RF-04 | El sistema debe asignar un rol (Estudiante, Padre, Docente, Administrador) y mostrar solo las funciones de ese rol. | Sistema | Alta |
| RF-05 | El sistema debe permitir editar el perfil: nombre, avatar predefinido y grado (10.° u 11.° para estudiantes). | Usuario | Media |
| RF-06 | El sistema debe registrar el consentimiento del padre o cuidador antes de activar la cuenta de un estudiante menor de edad. | Padre | Alta |

## 5.2 Vínculo familiar

| ID | Requisito | Actor | Prioridad |
| --- | --- | --- | --- |
| RF-07 | El sistema debe permitir que un padre vincule uno o más hijos mediante un código de familia o una invitación por correo. | Padre | Alta |
| RF-08 | El estudiante debe aceptar la vinculación antes de que el padre vea su progreso. | Estudiante | Alta |
| RF-09 | El padre debe ver el progreso resumido de cada hijo vinculado: módulos completados, puntos e insignias (no las respuestas individuales). | Padre | Alta |
| RF-10 | El sistema debe permitir lanzar un «reto familiar»: padre e hijo juegan el mismo juego y comparan puntajes. | Padre, Estudiante | Media |

## 5.3 Rutas, módulos y lecciones

| ID | Requisito | Actor | Prioridad |
| --- | --- | --- | --- |
| RF-11 | El sistema debe mostrar la ruta correspondiente al rol: Ruta Padres (P0–P9) o Ruta Estudiantes (E0–E8). | Estudiante, Padre | Alta |
| RF-12 | El sistema debe presentar cada módulo como un mapa de pasos: lección → juego → quiz de cierre. | Estudiante, Padre | Alta |
| RF-13 | Las lecciones deben combinar texto corto, imagen o video de máximo 3 minutos e infografía. | Estudiante, Padre | Alta |
| RF-14 | El sistema debe desbloquear el siguiente módulo al completar el quiz de cierre con al menos 60 %, salvo que el docente lo desactive. | Sistema | Media |
| RF-15 | El sistema debe guardar el avance automáticamente y permitir retomar donde se dejó. | Sistema | Alta |
| RF-16 | El sistema debe permitir descargar un certificado PDF al terminar la ruta completa. | Estudiante, Padre | Baja |

## 5.4 Juegos y gamificación

| ID | Requisito | Actor | Prioridad |
| --- | --- | --- | --- |
| RF-17 | El sistema debe ofrecer las 10 mecánicas del catálogo (J01–J10) como plantillas configurables. | Sistema | Alta |
| RF-18 | El sistema debe generar crucigramas y sopas de letras automáticamente a partir de la lista de palabras. | Sistema | Alta |
| RF-19 | El sistema debe calcular el puntaje de cada partida según las reglas de la mecánica. | Sistema | Alta |
| RF-20 | El sistema debe mostrar retroalimentación explicativa tras cada respuesta incorrecta. | Sistema | Alta |
| RF-21 | El sistema debe permitir reintentar un juego y conservar el mejor puntaje y el número de intentos. | Estudiante, Padre | Alta |
| RF-22 | El sistema debe otorgar insignias por hitos (primer módulo, racha de 5 días, puntaje perfecto, ruta completa). | Sistema | Media |
| RF-23 | El sistema debe mostrar una tabla de posiciones por grupo, que el docente puede ocultar. | Estudiante | Media |
| RF-24 | Al terminar un juego, el sistema debe pedir una calificación de agrado de 1 a 5 estrellas (opcional, un toque). | Estudiante, Padre | Alta |
| RF-25 | El sistema debe registrar por cada partida: usuario, juego, concepto de cada pregunta, aciertos, errores, tiempo, abandono y calificación. | Sistema | Alta |
| RF-26 | El sistema debe mantener una racha diaria y enviar un recordatorio si se pierde. | Sistema, Planificador | Baja |

## 5.5 Gestión docente de grupos y contenido

| ID | Requisito | Actor | Prioridad |
| --- | --- | --- | --- |
| RF-27 | El docente debe poder crear grupos (p. ej. «11-A 2026») y obtener su código de clase. | Docente | Alta |
| RF-28 | El docente debe poder asignar módulos a un grupo con fecha de apertura y fecha límite. | Docente | Alta |
| RF-29 | El docente debe poder crear y editar juegos eligiendo una plantilla y cargando su contenido. | Docente | Alta |
| RF-30 | El docente debe poder importar preguntas o palabras desde un archivo CSV. | Docente | Media |
| RF-31 | El docente debe poder previsualizar un juego antes de publicarlo. | Docente | Alta |
| RF-32 | El docente debe poder etiquetar cada pregunta con un concepto (p. ej. «phishing», «contraseñas»). | Docente | Alta |
| RF-33 | El docente debe poder publicar anuncios para un grupo o para los padres del grupo. | Docente | Media |
| RF-34 | El docente debe poder ver y responder las dudas enviadas desde los módulos P9 y E8. | Docente | Media |

## 5.6 Dashboard docente y analítica

| ID | Requisito | Actor | Prioridad |
| --- | --- | --- | --- |
| RF-35 | El dashboard debe mostrar indicadores clave: estudiantes inscritos, activos en 7 días, % de avance promedio y puntaje promedio. | Docente | Alta |
| RF-36 | El dashboard debe mostrar cuántos estudiantes y cuántos padres completaron cada módulo. | Docente | Alta |
| RF-37 | El dashboard debe mostrar el avance de cada estudiante (módulos completados ÷ asignados) y resaltar a quienes llevan más de 7 días inactivos. | Docente | Alta |
| RF-38 | El dashboard debe mostrar el puntaje promedio por módulo y por juego, indicando dónde se obtuvieron más puntos. | Docente | Alta |
| RF-39 | El dashboard debe mostrar las actividades mejor calificadas (estrellas) y las más jugadas. | Docente | Alta |
| RF-40 | El dashboard debe detectar falencias: conceptos con tasa de error superior al 40 % y preguntas más falladas. | Docente | Alta |
| RF-41 | El dashboard debe mostrar la actividad en el tiempo (partidas por día o semana). | Docente | Media |
| RF-42 | El dashboard debe permitir filtrar por grupo, grado, rol (estudiante o padre), módulo y rango de fechas. | Docente | Alta |
| RF-43 | El dashboard debe permitir ver el detalle de un estudiante: partidas, puntajes, intentos y conceptos débiles. | Docente | Alta |
| RF-44 | El sistema debe permitir exportar los reportes a CSV y PDF. | Docente | Media |
| RF-45 | El sistema debe enviar al docente un resumen semanal por correo con alertas de falencias e inactividad. | Planificador, Correo | Baja |

## 5.7 Administración

| ID | Requisito | Actor | Prioridad |
| --- | --- | --- | --- |
| RF-46 | El administrador debe poder gestionar instituciones, docentes y usuarios (crear, desactivar, restablecer contraseña). | Administrador | Alta |
| RF-47 | El administrador debe poder gestionar el catálogo base de módulos y rutas que heredan todos los docentes. | Administrador | Alta |
| RF-48 | El administrador debe poder ver métricas globales de uso por institución y la bitácora de auditoría. | Administrador | Media |
