# Diagramas de casos de uso por actor

La fuente UML oficial de cada diagrama es su archivo `.puml` en [`casos-de-uso/`](casos-de-uso/). Debajo de cada enlace hay una vista previa en Mermaid, que GitHub muestra directamente.

Convenciones:

- Óvalo = caso de uso.
- Flecha continua = el actor participa en el caso.
- Flecha punteada `«include»`: va del caso base al caso incluido, que siempre se ejecuta.
- Flecha punteada `«extend»`: va de la extensión al caso base, y la extensión solo ocurre a veces.

## 1. Generalización de actores y casos comunes

Fuente: [`00-usuarios.puml`](casos-de-uso/00-usuarios.puml)

```mermaid
flowchart LR
    E((Estudiante)) --> U((Usuario))
    P((Padre / Cuidador)) --> U
    D((Docente)) --> U
    A((Administrador)) --> U
    subgraph S[CiberFamilias]
        CU01([CU-01 Registrarse])
        CU02([CU-02 Iniciar sesión])
        REC([Recuperar contraseña])
        PER([Editar perfil])
    end
    U --> CU01
    U --> CU02
    U --> PER
    REC -.->|«extend»| CU02
    REC --> M((Servicio de correo))
```

## 2. Estudiante

Fuente: [`01-estudiante.puml`](casos-de-uso/01-estudiante.puml)

```mermaid
flowchart LR
    E((Estudiante))
    subgraph S[CiberFamilias]
        CU03([CU-03 Unirse a grupo con código])
        CU05([CU-05 Aceptar vinculación con padre])
        CU07([CU-07 Explorar ruta de aprendizaje])
        CU08([CU-08 Ver lección])
        CU09([CU-09 Jugar minijuego])
        CU10([CU-10 Responder quiz de cierre])
        CU12([CU-12 Ver mi progreso e insignias])
        CU14([CU-14 Jugar reto familiar])
        CU15([CU-15 Enviar duda])
        RR([Registrar resultado])
        RET([Ver retroalimentación])
        INS([Obtener insignia])
        CU11([CU-11 Calificar actividad])
        RANK([Ver tabla de posiciones])
    end
    E --> CU03 & CU05 & CU07 & CU08 & CU09 & CU10 & CU12 & CU14 & CU15
    CU09 -.->|«include»| RR
    CU10 -.->|«include»| RR
    CU14 -.->|«include»| CU09
    RET -.->|«extend»| CU09
    INS -.->|«extend»| CU09
    CU11 -.->|«extend»| CU09
    RANK -.->|«extend»| CU12
```

## 3. Padre / Cuidador

Fuente: [`02-padre.puml`](casos-de-uso/02-padre.puml)

```mermaid
flowchart LR
    P((Padre / Cuidador))
    subgraph S[CiberFamilias]
        CU03([CU-03 Unirse a grupo con código])
        CU04([CU-04 Vincular hijo])
        CU06([CU-06 Otorgar consentimiento])
        CU07([CU-07 Explorar Ruta Padres])
        CU08([CU-08 Ver lección])
        CU09([CU-09 Jugar minijuego])
        CU12([CU-12 Ver mi progreso])
        CU13([CU-13 Ver progreso del hijo])
        CU14([CU-14 Lanzar reto familiar])
        CU15([CU-15 Enviar duda])
        INV([Enviar invitación])
        RR([Registrar resultado])
        CU11([CU-11 Calificar actividad])
    end
    M((Servicio de correo))
    P --> CU03 & CU04 & CU06 & CU07 & CU08 & CU09 & CU12 & CU13 & CU14 & CU15
    CU04 -.->|«include»| INV
    INV --> M
    CU09 -.->|«include»| RR
    CU14 -.->|«include»| CU09
    CU11 -.->|«extend»| CU09
```

CU-13 requiere un vínculo activo, es decir, CU-04 aceptado por el estudiante en CU-05.

## 4. Docente

Fuente: [`03-docente.puml`](casos-de-uso/03-docente.puml)

```mermaid
flowchart LR
    D((Docente))
    subgraph S[CiberFamilias]
        CU16([CU-16 Gestionar grupos])
        CU17([CU-17 Asignar módulos])
        CU18([CU-18 Crear / editar juego])
        CU19([CU-19 Publicar anuncio])
        CU20([CU-20 Consultar dashboard])
        CU22([CU-22 Responder dudas])
        COD([Generar código de clase])
        PLA([Elegir plantilla])
        TAG([Etiquetar conceptos])
        PRE([Previsualizar juego])
        CSV([Importar CSV])
        FIL([Filtrar datos])
        DET([Ver detalle de estudiante])
        FAL([Analizar falencias])
        CU21([CU-21 Exportar reporte])
    end
    D --> CU16 & CU17 & CU18 & CU19 & CU20 & CU22
    CU16 -.->|«include»| COD
    CU18 -.->|«include»| PLA
    CU18 -.->|«include»| TAG
    CU18 -.->|«include»| PRE
    CSV -.->|«extend»| CU18
    CU20 -.->|«include»| FIL
    DET -.->|«extend»| CU20
    FAL -.->|«extend»| CU20
    CU21 -.->|«extend»| CU20
```

## 5. Administrador

Fuente: [`04-administrador.puml`](casos-de-uso/04-administrador.puml)

```mermaid
flowchart LR
    A((Administrador))
    subgraph S[CiberFamilias]
        CU23([CU-23 Gestionar usuarios e instituciones])
        CU24([CU-24 Gestionar catálogo base])
        CU25([CU-25 Ver métricas globales y auditoría])
        ROL([Asignar rol])
        DES([Desactivar usuario])
        RES([Restablecer contraseña])
        RUT([Gestionar rutas y módulos])
        PLT([Gestionar plantillas de juego])
    end
    A --> CU23 & CU24 & CU25
    CU23 -.->|«include»| ROL
    DES -.->|«extend»| CU23
    RES -.->|«extend»| CU23
    CU24 -.->|«include»| RUT
    CU24 -.->|«include»| PLT
```

## 6. Actores de sistema (Planificador y Servicio de correo)

Fuente: [`05-sistema.puml`](casos-de-uso/05-sistema.puml)

```mermaid
flowchart LR
    T((Planificador))
    subgraph S[CiberFamilias]
        CU26([CU-26 Calcular métricas agregadas])
        ALE([Detectar alertas: inactividad, falencias])
        RES([Enviar resumen semanal])
        RAC([Enviar recordatorio de racha])
    end
    M((Servicio de correo))
    D((Docente))
    T --> CU26
    T --> RAC
    CU26 -.->|«include»| ALE
    RES -.->|«extend»| CU26
    RES --> M
    RAC --> M
    RES --> D
```
