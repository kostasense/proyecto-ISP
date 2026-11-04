# Proyecto Integrador: ISP local con monitoreo, seguridad y administración de red

Diseño y operación de un ISP local, con enfoque en FCAPS, montado en PNETLab.

## Contenido

- [00 Introducción](00-Introduccion.md)
- [01 Topología y arquitectura](01-Topologia-y-Arquitectura.md)
- [02 Servicios implementados](02-Servicios-Implementados.md)
- [03 Monitoreo y FCAPS](03-Monitoreo-y-FCAPS.md)
- [04 Políticas de seguridad](04-Politicas-de-Seguridad.md)
- [05 SLA y mesa de ayuda](05-SLA-y-Mesa-de-Ayuda.md)
- [06 Registro de incidencias](06-Registro-de-Incidencias.md)
- [07 Resumen final](07-Resumen-Final.md)

## Estructura de evidencias

```text
evidencias/
  capturas/      # capturas de configuración, pruebas, tickets, logs
  diagramas/     # topologías, flujos y diagramas
  reportes/      # gráficas, análisis, tablas de tiempos
  dashboards/    # vistas del NOC
```

## Convenciones

- **Nombre de evidencias:** `AAAA-MM-DD_rol_tema.ext`
  (ejemplo: `2026-11-05_monitoreo_alerta-enlace-isp1.png`).
- **Enlaces:** cada evidencia se enlaza desde el `.md` que la usa, el mismo día que se sube.
- **Commits del repositorio:** `<letra>: descripción breve`
  (ejemplo: `F: agrega catálogo de casos de falla`).
- **Capturas:** deben mostrar fecha y hora visibles.
- **Secretos:** nunca subir contraseñas, claves ni configuraciones sin limpiar.