# 00. Introducción

## 1. Descripción del proyecto

**Empresa:** [Nombre del ISP pendiente]

Este proyecto consiste en diseñar, implementar y documentar la infraestructura técnica
y operativa de una empresa proveedora de servicios de Internet (ISP) para una comunidad
rural y comunidades vecinas. El trabajo aplica las funciones de administración de redes
vistas en el curso: configuración, fallas, contabilidad, desempeño y seguridad (FCAPS).

El laboratorio se construye de forma lógica en **PNETLab**.

## 2. Objetivo

Diseñar e implementar un modelo operativo de ISP que ofrezca conectividad a clientes
residenciales y pequeños negocios, integrando servicios de red, monitoreo, soporte técnico,
seguridad, medición de consumo y administración de la infraestructura, con un enfoque
académico y práctico.

## 3. Alcance y escenario

- Atender como mínimo **10 clientes**, con una población potencial de **200 usuarios** y
  posibilidad de expansión a comunidades vecinas.
- Salida a Internet con **3 proveedores**: ISP 1 e ISP 2 con balanceo de carga e ISP 3
  como respaldo (failover).
- Infraestructura híbrida: se simula en PNETLab lo que en una implementación real sería
  físico.
- Equipo de seis integrantes. El enfoque central es FCAPS: cada letra tiene un responsable.

## 4. Notas académica y regulatoria

> **Nota 1.** Este proyecto es un ejercicio académico y no debe considerarse una guía para
> operar una empresa de telecomunicaciones real ni una infraestructura de producción con
> impacto en servicios públicos.
>
> **Nota 2.** En la práctica real, la reventa de servicios y la operación de un ISP requiere
> cumplir las regulaciones comerciales, legales y de telecomunicaciones locales y nacionales.

## 5. Arquitectura general (resumen)

> El detalle (VLAN, direccionamiento, justificación) está en
> [01-Topologia-y-Arquitectura.md](01-Topologia-y-Arquitectura.md).

- **Perímetro:** núcleo, proxy transparente, firewall/NAT con balanceo y failover, ISP 1,
  ISP 2 e ISP 3, e Internet.
- **Red interna:** 1 switch de núcleo, 2 de distribución (en triángulo con el núcleo) y
  10 equipos de acceso (ACC-01 a ACC-10).
- **Servidores y servicios:** autenticación, DHCP, DNS, HTTPS, monitoreo, almacenamiento y
  media server, repartidos entre los dos switches de distribución.
- **Clientes:** 10 clientes simulados, residenciales y pequeños negocios.

## 6. Roles y enfoque FCAPS

| Rol | Letra | Integrante | Escribe (archivos y secciones) | Apoya en |
|---|---|---|---|---|
| Jefe de proyecto / gerente de operaciones | F (fallas) | Vizcaíno Rodríguez Ángel Leonardo | 00; sección F de 03; caso integrado de 03; 07; repositorio y `evidencias/` | 01 (registro de decisiones), 06 (casos y tiempos), 05 (prioridades) |
| Admin. de infraestructura y servicios | C (configuración) | Martínez Toloza Darina Elizabeth | 01; 02 (red, DHCP, DNS, NAT, firewall, proxy, HTTPS); sección C de 03 (inventario, respaldos, cambios) | 04 (aplicar ACL y SSH), 06 (ejecutar fallas y recuperación), 03 (lista de equipos a monitorear) |
| Admin. de monitoreo y alertas | A (consumo) | Olivas Quiñonez Grecia | 03: sección A, NOC, alertas, logs centralizados, NTP y tráfico por cliente y proveedor | 03 sección F (alertas y tiempo de detección), 03 sección P (datos de utilización), 04 (recibe logs de seguridad) |
| Especialista en seguridad y control de acceso | P (desempeño) | Román Zazueta Ángel Gabriel | 03: sección P (KPI, umbrales, línea base, caso de degradación); 02: control de ancho de banda | 05 (propuesta de SLA), 04 (ACL, firewall, SSH), 02 (HTTPS y proxy), 06 (comparar tiempos con umbrales) |
| Especialista en soporte técnico y mesa de ayuda | S (seguridad y tickets) | Meza Vidaña Lanna Yakira | 04; 05 (mesa de ayuda, tickets, escalamiento, bitácoras, SLA final); 06; sección S de 03; 02 (autenticación) | 03 sección F (ticket de cada caso), 03 sección C (bitácora de cambios) |
| Analista de métricas y reportes | Documentación de servicios | Bejarano Félix Bernardo Daniel | 02 (almacenamiento y media server); consolidación de `evidencias/reportes/` | 01 (diagramas), 03 secciones A y P (gráficas y reportes), 06 (evidencias de cada caso), 07 (resultados), 05 (SLA: apoya con datos) |

Cada integrante tiene un **trabajo base** (su letra) y un **trabajo de apoyo** a otros roles
en cada fase. Las actividades por fase están en el plan de trabajo del equipo.

## 7. Estructura del repositorio

| Archivo | Contenido | Responsable | Apoyan |
|---|---|---|---|
| 00-Introduccion.md | Descripción, alcance, roles, responsables | Jefe (F) | Todos |
| 01-Topologia-y-Arquitectura.md | Topología, VLAN, direccionamiento, decisiones, flujos | Infra (C) | Analista (diagramas), Jefe (decisiones), Seguridad (segmentación) |
| 02-Servicios-Implementados.md | Configuración y pruebas de cada servicio | Infra (C); Analista (almacenamiento y media server); Soporte (autenticación) | Seguridad (HTTPS, proxy, ancho de banda) |
| 03-Monitoreo-y-FCAPS.md | Secciones F, C, A, P, S, NOC y caso integrado | Una sección por rol: F Jefe, C Infra, A Monitoreo, P Seguridad, S Soporte | Analista (reportes); Jefe (caso integrado) |
| 04-Politicas-de-Seguridad.md | Segmentación, accesos, ACL, SSH, incidente de seguridad | Soporte (S) | Seguridad (P), Infra (aplicar en equipos) |
| 05-SLA-y-Mesa-de-Ayuda.md | SLA, prioridades, escalamiento, tickets, bitácoras | Soporte (S) | Seguridad (propuesta de SLA), Jefe (prioridades), Analista (datos) |
| 06-Registro-de-Incidencias.md | Una entrada por incidente simulado | Soporte (S) | Jefe (casos y tiempos), Analista (evidencias), cada rol en su caso |
| 07-Resumen-Final.md | Resultados, retos, soluciones y lecciones aprendidas | Jefe (F) | Todos: cada rol aporta sus retos y lecciones |
| evidencias/ | capturas, diagramas, reportes, dashboards | Jefe (estructura) | Cada rol sube las suyas; Analista consolida `reportes/` |

## 8. Responsables por área de trabajo

| Área de trabajo | Responsable | Apoya |
|---|---|---|
| Topología, VLAN, direccionamiento y diagramas | Infra (C) | Analista, Jefe |
| Proveedores, balanceo y failover | Infra (C) | Jefe |
| Servicios de red y clientes simulados | Infra (C) | Jefe, Soporte (autenticación), Seguridad (HTTPS, proxy) |
| Documentación de almacenamiento y media server | Analista | Infra |
| Inventario, respaldos y control de versiones de configuración | Infra (C) | Soporte |
| Monitoreo, herramienta elegida y NOC | Monitoreo (A) | Infra, Seguridad |
| Medición de consumo | Monitoreo (A) | Seguridad |
| Indicadores de desempeño y umbrales | Seguridad (P) | Monitoreo, Analista |
| Gestión de fallas y casos de simulación | Jefe (F) | Infra, Monitoreo, Soporte |
| Caso integrado F+C+A+P+S | Jefe (F) | Todos |
| Políticas de seguridad e incidente de seguridad | Soporte (S) | Seguridad (P) |
| SLA y escalamiento | Seguridad (propone) y Soporte (cierra) | Jefe |
| Mesa de ayuda, tickets y bitácoras | Soporte (S) | Jefe, Infra |
| Registro de incidencias | Soporte (S) | Jefe |
| Repositorio, evidencias y revisión cruzada | Jefe (F) | Todos |
| Resumen final y presentación | Jefe (F) | Analista, todos |

## 9. Convenciones de trabajo

- Las evidencias se suben el mismo día, con nombre `AAAA-MM-DD_rol_tema.ext`, y se enlazan
  desde el archivo `.md` correspondiente.
- Una tarea se considera terminada sólo si está **implementada, probada (con evidencia) y
  documentada**.
- Todo cambio en la red se registra antes de ejecutarse y tiene respaldo previo.
- Toda simulación genera un ticket y una entrada en `06-Registro-de-Incidencias.md`.