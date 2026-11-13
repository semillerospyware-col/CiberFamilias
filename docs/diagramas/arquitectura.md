# Diagramas de componentes y de despliegue

La arquitectura propuesta tiene tres capas (navegador, API y datos) y un worker que precalcula las métricas del dashboard. Las tecnologías nombradas (React, Node.js, PostgreSQL) son una sugerencia y pueden cambiarse.

<p align="center">
  <img src="arquitectura.svg" alt="Vista de componentes por nodo" width="720">
</p>

El motor de juegos envía cada acierto, error y abandono al componente de Eventos y analítica. El worker los agrega cada hora y el dashboard lee esos agregados. Las invitaciones y los resúmenes salen por una cola de correos que procesa el worker.

## Diagrama de componentes

Fuente UML: [`componentes.puml`](componentes.puml)

```mermaid
flowchart TB
    subgraph CLI[Cliente - navegador]
        SPA[SPA React]
        GAME[Motor de juegos]
        DASH[Dashboard docente]
    end
    subgraph API[API - Node.js]
        AUTH[Autenticación y roles]
        USR[Usuarios y familias]
        CONT[Contenido y rutas]
        SCORE[Puntaje y gamificación]
        EVT[Eventos y analítica]
        REP[Reportes]
    end
    DB[(PostgreSQL)]
    S3[(Almacenamiento de objetos)]
    WK[Worker planificador]
    MAIL{{Servicio de correo}}

    SPA -->|inicia sesión| AUTH
    SPA -->|grupos y vínculos| USR
    SPA -->|rutas y lecciones| CONT
    GAME -->|carga contenido| CONT
    GAME -->|envía resultado| SCORE
    GAME -->|envía eventos| EVT
    DASH -->|consulta métricas| EVT
    DASH -->|exporta| REP
    SCORE --> EVT
    AUTH & USR & CONT & EVT & REP --> DB
    CONT --> S3
    WK -->|agrega métricas| DB
    WK -->|envía correos| MAIL
```

## Diagrama de despliegue

Fuente UML: [`despliegue.puml`](despliegue.puml)

```mermaid
flowchart TB
    subgraph DEV[«dispositivo» Dispositivo del usuario]
        subgraph NAV[Navegador web]
            spa[SPA React]
        end
    end
    subgraph CDN[«servidor» CDN / hosting estático]
        static[index.html + JS + CSS]
    end
    subgraph APP[«contenedor Docker» Servidor de aplicaciones]
        api[API Node.js]
    end
    subgraph JOB[«contenedor Docker» Servidor de tareas]
        wk[Worker planificador - cron]
    end
    db[(PostgreSQL 16)]
    s3[(Almacenamiento de objetos S3)]
    mail{{Servicio de correo}}

    spa -.->|HTTPS descarga| static
    spa -->|HTTPS REST/JSON| api
    spa -->|HTTPS URLs firmadas| s3
    api -->|TCP 5432| db
    api -->|HTTPS| s3
    wk -->|TCP 5432| db
    wk -->|SMTP 587| mail
```
