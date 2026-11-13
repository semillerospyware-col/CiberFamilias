# 6. Requisitos no funcionales

| ID | Categoría | Requisito |
| --- | --- | --- |
| RNF-01 | Usabilidad | Interfaz minimalista: máximo una acción principal por pantalla; cualquier juego a 3 clics o menos desde el inicio. |
| RNF-02 | Usabilidad | Lenguaje sencillo, apto para padres sin formación técnica; glosario emergente en cada término técnico. |
| RNF-03 | Accesibilidad | Cumplir WCAG 2.1 AA: contraste 4.5:1, navegación por teclado y textos alternativos en imágenes. |
| RNF-04 | Compatibilidad | Diseño responsive desde 360 px de ancho; Chrome, Edge, Firefox y Safari en sus 2 últimas versiones. |
| RNF-05 | Rendimiento | Carga inicial de un juego en menos de 3 s con conexión 4G; dashboard en menos de 2 s con 500 estudiantes. |
| RNF-06 | Disponibilidad | 99 % de disponibilidad mensual en horario escolar (6:00 a 22:00). |
| RNF-07 | Escalabilidad | Soportar al menos 1.000 usuarios concurrentes por institución sin degradación. |
| RNF-08 | Seguridad | HTTPS obligatorio, contraseñas con hash bcrypt o argon2, sesiones con JWT de vida corta y bloqueo tras 5 intentos fallidos. |
| RNF-09 | Seguridad | Control de acceso por rol en el backend y políticas por fila en la base de datos (un docente solo ve sus grupos; un padre solo ve a sus hijos). |
| RNF-10 | Privacidad | Cumplir la Ley 1581 de 2012 (Habeas Data, Colombia): consentimiento del acudiente para menores, minimización de datos y derecho de supresión. |
| RNF-11 | Privacidad | Sin publicidad ni rastreadores de terceros; los datos de analítica no salen de la plataforma. |
| RNF-12 | Mantenibilidad | Cada mecánica de juego es un componente independiente con interfaz común (cargar contenido, emitir eventos, devolver puntaje). |
| RNF-13 | Respaldo | Copia de seguridad diaria de la base de datos, con retención de 30 días. |
| RNF-14 | Auditoría | Registrar en bitácora los cambios de rol, de contenido y las exportaciones de datos. |
