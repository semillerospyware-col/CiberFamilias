# 7. Casos de uso

Son 26 casos de uso. Se detallan los 5 que concentran la lógica central: jugar, crear juego, dashboard, vínculo familiar y unirse a un grupo. Los diagramas por actor están en [`diagramas/casos-de-uso.md`](diagramas/casos-de-uso.md).

## 7.1 Listado

| ID | Caso de uso | Actor(es) | RF |
| --- | --- | --- | --- |
| CU-01 | Registrarse | Usuario | RF-01 |
| CU-02 | Iniciar sesión / recuperar contraseña | Usuario, Correo | RF-03 |
| CU-03 | Unirse a grupo con código | Estudiante, Padre | RF-02 |
| CU-04 | Vincular hijo | Padre, Correo | RF-07 |
| CU-05 | Aceptar vinculación | Estudiante | RF-08 |
| CU-06 | Otorgar consentimiento | Padre | RF-06 |
| CU-07 | Explorar ruta de aprendizaje | Estudiante, Padre | RF-11, RF-12 |
| CU-08 | Ver lección | Estudiante, Padre | RF-13 |
| CU-09 | Jugar minijuego | Estudiante, Padre | RF-17 a RF-21, RF-25 |
| CU-10 | Responder quiz de cierre | Estudiante, Padre | RF-14 |
| CU-11 | Calificar actividad | Estudiante, Padre | RF-24 |
| CU-12 | Ver mi progreso e insignias | Estudiante, Padre | RF-15, RF-22, RF-23 |
| CU-13 | Ver progreso del hijo | Padre | RF-09 |
| CU-14 | Lanzar reto familiar | Padre, Estudiante | RF-10 |
| CU-15 | Enviar duda | Estudiante, Padre | RF-34 |
| CU-16 | Gestionar grupos | Docente | RF-27 |
| CU-17 | Asignar módulos | Docente | RF-28 |
| CU-18 | Crear / editar juego | Docente | RF-29 a RF-32 |
| CU-19 | Publicar anuncio | Docente | RF-33 |
| CU-20 | Consultar dashboard | Docente | RF-35 a RF-43 |
| CU-21 | Exportar reporte | Docente | RF-44 |
| CU-22 | Responder dudas | Docente | RF-34 |
| CU-23 | Gestionar usuarios e instituciones | Administrador | RF-46 |
| CU-24 | Gestionar catálogo base | Administrador | RF-47 |
| CU-25 | Ver métricas globales y auditoría | Administrador | RF-48 |
| CU-26 | Calcular métricas y enviar resumen semanal | Planificador, Correo | RF-26, RF-45 |

---

## 7.2 CU-09 Jugar minijuego

| Campo | Descripción |
| --- | --- |
| Actores | Estudiante o Padre (primario) |
| Precondición | Sesión iniciada; módulo asignado y desbloqueado |
| Postcondición | Partida registrada con puntaje, eventos por pregunta y calificación; progreso actualizado |
| Incluye | Registrar resultado |
| Extensiones | Ver retroalimentación (al fallar), Calificar actividad (CU-11), Obtener insignia |

**Flujo principal**

1. El usuario abre un módulo y selecciona el juego.
2. El sistema muestra las instrucciones en una pantalla (máximo 3 líneas) y el botón «Jugar».
3. El sistema carga la plantilla de la mecánica con el contenido configurado por el docente.
4. El usuario responde o interactúa; por cada acción el sistema evalúa y muestra acierto o error.
5. Al terminar, el sistema calcula el puntaje y muestra un resumen: puntos, aciertos, tiempo y mejor puntaje.
6. El sistema pide calificar el juego de 1 a 5 estrellas.
7. El sistema registra la partida y actualiza el avance del módulo.

**Flujos alternos**

- **4a.** Respuesta incorrecta: el sistema muestra la explicación del concepto y continúa.
- **4b.** El usuario abandona: el sistema registra la partida como «abandonada» con el avance parcial.
- **5a.** El puntaje supera un hito: el sistema otorga la insignia correspondiente.
- **6a.** El usuario omite la calificación: se guarda sin estrellas.
- **7a.** Sin conexión: el sistema guarda los eventos localmente y los sincroniza al reconectar.

---

## 7.3 CU-18 Crear / editar juego

| Campo | Descripción |
| --- | --- |
| Actor | Docente |
| Precondición | El docente tiene al menos un módulo a su cargo |
| Postcondición | Juego publicado y visible para los grupos que tienen asignado el módulo |
| Incluye | Elegir plantilla, Etiquetar conceptos, Previsualizar juego |
| Extensiones | Importar contenido desde CSV |

**Flujo principal**

1. El docente entra a un módulo y elige «Nuevo juego».
2. El sistema muestra las 10 plantillas (J01–J10) con una vista previa animada.
3. El docente elige una plantilla y carga el contenido (palabras, preguntas, pares o escenarios).
4. El docente etiqueta cada ítem con un concepto.
5. El sistema valida el contenido (p. ej. mínimo 6 palabras para una sopa de letras) y genera el juego.
6. El docente previsualiza y juega la versión de prueba.
7. El docente publica; el sistema lo marca como activo.

**Flujos alternos**

- **3a.** El docente importa un CSV: el sistema valida las columnas y muestra los errores por fila.
- **5a.** Contenido insuficiente o inválido: el sistema indica qué falta y no permite publicar.
- **7a.** El juego ya tiene partidas: el sistema crea una nueva versión y conserva las estadísticas de la anterior.

---

## 7.4 CU-20 Consultar dashboard

| Campo | Descripción |
| --- | --- |
| Actor | Docente |
| Precondición | El docente tiene al menos un grupo con integrantes |
| Postcondición | Ninguna (consulta) |
| Incluye | Filtrar datos |
| Extensiones | Ver detalle de estudiante, Analizar falencias, Exportar reporte (CU-21) |

**Flujo principal**

1. El docente abre el dashboard.
2. El sistema muestra los indicadores clave del grupo por defecto y de los últimos 30 días.
3. El sistema muestra las gráficas: avance por módulo, puntaje por juego, actividades favoritas, actividad en el tiempo y mapa de falencias.
4. El docente aplica filtros (grupo, grado, rol, módulo, fechas); el sistema recalcula todas las vistas.
5. El docente selecciona un concepto con falencia; el sistema lista las preguntas más falladas y los estudiantes afectados.

**Flujos alternos**

- **2a.** Grupo sin partidas: el sistema muestra un estado vacío con el enlace para asignar módulos.
- **5a.** El docente abre a un estudiante: el sistema muestra su historial de partidas, intentos y conceptos débiles.
- **5b.** El docente exporta: el sistema genera un CSV o PDF con los filtros activos.

---

## 7.5 CU-04 Vincular hijo

| Campo | Descripción |
| --- | --- |
| Actores | Padre (primario), Servicio de correo, Estudiante (en CU-05) |
| Precondición | El padre tiene cuenta activa |
| Postcondición | Vínculo en estado «pendiente» hasta que el estudiante acepte |
| Incluye | Enviar invitación |

**Flujo principal**

1. El padre elige «Vincular hijo» e ingresa el correo o el código de familia del estudiante.
2. El sistema verifica que el estudiante exista y esté en grado 10.° u 11.°.
3. El sistema envía la solicitud al estudiante (notificación y correo).
4. El estudiante acepta (CU-05); el sistema activa el vínculo y el padre ve el progreso del hijo.

**Flujos alternos**

- **2a.** El estudiante no existe: el sistema envía una invitación de registro con el vínculo precargado.
- **4a.** El estudiante rechaza: el vínculo se cancela y se notifica al padre.

---

## 7.6 CU-03 Unirse a grupo con código

| Campo | Descripción |
| --- | --- |
| Actores | Estudiante o Padre |
| Precondición | Sesión iniciada; el docente compartió el código |
| Postcondición | Usuario inscrito en el grupo con la ruta de su rol asignada |

**Flujo principal**

1. El usuario ingresa el código de clase de 7 caracteres.
2. El sistema valida el código y muestra el nombre del grupo y del docente.
3. El usuario confirma; el sistema lo inscribe y muestra su ruta.

**Flujos alternos**

- **2a.** Código inválido o vencido: el sistema muestra el error y permite reintentar (máximo 5 intentos por hora).
