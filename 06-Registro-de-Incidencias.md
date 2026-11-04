# 06. Registro de incidencias

Cada incidente simulado genera un ticket y una entrada en este archivo.
Los casos y las definiciones de tiempo están en la
[sección F de 03-Monitoreo-y-FCAPS.md](03-Monitoreo-y-FCAPS.md#f-gestión-de-fallas).

## Cómo llenarlo

1. Copiar la ficha de la plantilla y numerarla (`INC-001`, `INC-002`...).
2. Llenar las marcas de tiempo T0 a T5 con la hora del equipo (sincronizada por NTP).
3. Enlazar cada evidencia con su ruta en `evidencias/`.
4. Agregar una fila al resumen del final.

## Plantilla de ficha

### INC-XXX. [Título corto]

| Campo | Detalle |
|---|---|
| Caso (ID del catálogo) | F-0X |
| Ticket | [número] |
| Prioridad | P1 / P2 / P3 / P4 |
| Detectado por | [rol o alerta] |
| Síntoma | [qué se observó] |
| Diagnóstico | [qué se encontró, capa por capa] |
| Origen identificado | [componente y causa] |
| Componente aislado | [cuál y cómo] |
| Solución aplicada | [pasos] |
| T0 / T1 / T2 / T3 / T4 / T5 | [AAAA-MM-DD hh:mm:ss] cada una |
| Tiempo de detección (T1 − T0) | [min:s] |
| **Tiempo de recuperación (T4 − T0)** | [min:s] |
| Funciones FCAPS involucradas | [F, C, A, P, S] |
| Evidencias | [rutas en `evidencias/`] |
| Lecciones aprendidas | [qué se mejora] |
| Cerrado | [ ] |

## Resumen de incidentes

| Núm. | Fecha y hora | Caso | Diagnóstico | Evidencias | Solución | T. detección | T. recuperación | FCAPS | Ticket | Cerrado |
|---|---|---|---|---|---|---|---|---|---|---|
| INC-001 | | | | | | | | | | [ ] |
| INC-002 | | | | | | | | | | [ ] |
| INC-003 | | | | | | | | | | [ ] |
| INC-004 | | | | | | | | | | [ ] |
| INC-005 | | | | | | | | | | [ ] |