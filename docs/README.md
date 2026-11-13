# Documentación de CiberFamilias

Documentación de análisis y diseño de la plataforma. Léase en orden.

| # | Documento | Contenido |
| --- | --- | --- |
| 1 | [Visión general](01-vision-general.md) | Objetivo, problema, alcance y principios de diseño |
| 2 | [Actores](02-actores.md) | Actores humanos y de sistema |
| 3 | [Módulos de contenido](03-modulos.md) | Ruta Padres y Ruta Estudiantes con el juego de cada módulo |
| 4 | [Mecánicas de juego](04-mecanicas-de-juego.md) | Catálogo de 10 plantillas de juego y sus reglas de puntaje |
| 5 | [Requisitos funcionales](05-requisitos-funcionales.md) | RF-01 a RF-48 |
| 6 | [Requisitos no funcionales](06-requisitos-no-funcionales.md) | RNF-01 a RNF-14 |
| 7 | [Casos de uso](07-casos-de-uso.md) | CU-01 a CU-26, cinco detallados |
| 8 | [Dashboard docente](08-dashboard-docente.md) | Métricas, gráficas y alertas |
| — | [Diagramas UML](diagramas/README.md) | Casos de uso por actor, componentes y despliegue |

## Convenciones

- **RF-xx**: requisito funcional. **RNF-xx**: requisito no funcional. **CU-xx**: caso de uso.
- **P0–P9**: módulos de la Ruta Padres. **E0–E8**: módulos de la Ruta Estudiantes. **J01–J10**: mecánicas de juego.
- Prioridad: **Alta** (imprescindible en la v1), **Media** (deseable en la v1), **Baja** (versiones posteriores).
- Los diagramas fuente están en PlantUML (`.puml`). Cada documento de diagramas incluye además una vista previa en Mermaid, que GitHub muestra directamente.
