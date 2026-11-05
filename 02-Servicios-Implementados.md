# Servicios Implementados

## Bases conceptuales y justificación técnica de los servicios de aplicación (Almacenamiento y Medios)

Dentro de la arquitectura de red y servicios del ISP local simulado, se han desplegado dos servidores críticos sobre entornos de **Ubuntu Server**. La selección de estas plataformas responde a criterios estrictos de estabilidad, seguridad, eficiencia en el consumo de recursos y alineación con los requerimientos operativos de las funciones FCAPS.

---

### A. Servidor de Almacenamiento (SRV-STO) — NextCloud

- **Tecnología seleccionada:** NextCloud.
- **Ubicación en la red:** Asignado en la **VLAN 70 (Almacenamiento)**, operando bajo la dirección IP estática `10.0.70.10`.
- **Justificación de la elección y ventajas frente a otras opciones:**
  - **Frente a Samba (SMB) / NFS tradicional:** Aunque Samba y NFS son excelentes protocolos de bajo nivel para compartir carpetas puras en red, se limitan a ser discos duros compartidos sin una capa de gestión avanzada. **NextCloud** fue seleccionado porque ofrece una interfaz web completa, control estricto de usuarios por roles (RBAC) y un sistema robusto de auditoría y versionado de archivos. Esto permite no solo guardar los respaldos automáticos de las configuraciones de los equipos de red, sino también gestionar de forma gráfica y segura la documentación corporativa del ISP.
  - **Frente a soluciones comerciales en la nube (Google Drive, OneDrive):** Al tratarse de un entorno académico y de simulación de un ISP soberano, NextCloud garantiza que los datos permanezcan 100% dentro de la infraestructura local del laboratorio (en PNETLab), evitando dependencias externas y permitiendo evaluar escenarios de seguridad y control de acceso de manera completamente aislada.
- **Propósito operativo y funciones:**
  - Funciona como la nube privada centralizada de la empresa ISP.
  - Almacena de forma segura los respaldos automáticos y programados de las configuraciones de los equipos de red (routers, switches de núcleo y distribución), cumpliendo directamente con los requerimientos de la gestión de configuración (_Configuration_ de FCAPS).
  - Centraliza la documentación técnica, manuales operativos, bitácoras y reportes generados por el equipo de trabajo.
- **Modelo de control de acceso y cuentas mock:**
  - Se implementa un esquema estricto de control de acceso basado en roles (_RBAC_), mapeando a los 6 roles oficiales del equipo de trabajo (Gerente de Operaciones, Infraestructura, Seguridad, Monitoreo, Soporte y Analítica).
  - Se configuran cuentas de prueba (_mock_) con privilegios diferenciados para demostrar la capacidad de segmentación: cuentas administrativas con privilegios de escritura total para el mantenimiento de respaldos (ej. `admin.infra`), y cuentas con restricciones estrictas de solo lectura o acceso limitado a directorios específicos (ej. `auditor.seguridad` y `soporte.tecnico`), validando que la información corporativa y sensible esté protegida contra modificaciones accidentales o no autorizadas.
- **Puertos de red clave:** Opera mediante protocolos web seguros sobre los puertos estándar HTTP/HTTPS (`80` / `443`).

---

### B. Servidor de Medios (SRV-MEDIA) — Jellyfin

- **Tecnología seleccionada:** Jellyfin.
- **Ubicación en la red:** Asignado en la **VLAN 80 (Media Server)**, operando bajo la dirección IP estática `10.0.80.10`.
- **Justificación de la elección y ventajas frente a otras opciones:**
  - **Frente a Plex u otras alternativas comerciales/privativas:** Se eligió **Jellyfin** porque es una plataforma de código abierto (_open source_) y totalmente libre. A diferencia de Plex, no depende de servidores de autenticación externos en internet, no requiere cuentas de pago para funciones avanzadas y no limita el rendimiento del hardware. Al correr de manera local dentro de la maqueta de PNETLab, garantiza un funcionamiento autónomo incluso si los enlaces de los proveedores de internet (ISP 1, ISP 2, ISP 3) sufren caídas totales.
  - **Eficiencia en simulación de tráfico:** Su arquitectura permite la transmisión de video (_streaming_) bajo demanda ajustando la tasa de bits, lo que lo convierte en la herramienta perfecta para generar cargas de trabajo estables y predecibles orientadas a pruebas de red.
- **Propósito operativo y funciones:**
  - Actúa como una plataforma local de reproducción multimedia dentro de la infraestructura del ISP.
  - Su objetivo principal dentro del escenario académico no es comercial, sino servir como una herramienta controlada para **generar tráfico pesado de red**.
  - Permite simular escenarios donde múltiples clientes residenciales y de negocios (VLANs 90 y 100) consumen contenido de video de alta definición simultáneamente. Esto facilita al equipo la medición de métricas de desempeño (_Performance_) y el análisis de consumo de ancho de banda (_Accounting_), permitiendo comprobar la efectividad de las políticas de Calidad de Servicio (QoS) y el comportamiento de los enlaces ante situaciones de alta demanda o saturación.
- **Puertos de red clave:** Utiliza de forma predeterminada el puerto HTTP `8096` para la gestión de la plataforma y el flujo de streaming.
