# Guía de Organización y Nomenclatura de Evidencias - ISP Local

El propósito de este documento es estandarizar la forma en que el equipo almacena, nombra y clasifica todas las evidencias gráficas, capturas, diagramas, reportes y dashboards generados a lo largo del Proyecto Integrador.

## 1. Estructura Oficial de Carpetas

Todas las evidencias del proyecto deben depositarse exclusivamente dentro de la carpeta raíz `Evidencias/`, respetando la siguiente jerarquía oficial:

```text
Evidenias/
├── capturas/
├── diagramas/
├── reportes/
└── dashboards/
```

## 2. Descripción de Directorios y Contenidos

- **`capturas/`**: Almacena las capturas de pantalla de la ejecución operativa de la red, pruebas de conectividad, funcionamiento de servicios y simulaciones de incidencias.
- **`diagramas/`**: Contiene los diagramas topológicos físicos y lógicos de la infraestructura desarrollada en PNETLab.
- **`reportes/`**: Agrupa los reportes de rendimiento, líneas base, estadísticas de consumo y exportaciones de datos técnicos.
- **`dashboards/`**: Guarda las vistas principales del Centro de Operaciones de Red (NOC) y paneles de monitoreo en tiempo real.

## 3. Regla de Nomenclatura de Archivos

Para mantener un orden riguroso y profesional en el repositorio, cualquier archivo de evidencia que se suba deberá nombrarse obligatoriamente siguiendo esta estructura:

`[Fase]-[Tema]-[Descripción_Breve].[extensión]`

_(Ejemplo: `F1-Configuracion-TopologiaPnetlab.png` o `F3-Fallos-CaidaISP1.png`)_

---

## 4. Catálogo de Abreviaturas para Nomenclatura

### Fases del Proyecto:

- Fase 0: Preparación y diseño -> **`F0`**
- Fase 1: Construcción base -> **`F1`**
- Fase 2: Operación y línea base -> **`F2`**
- Fase 3: Simulaciones FCAPS -> **`F3`**
- Fase 4: Integración y cierre -> **`F4`**

### Temas y Módulos (Modelo FCAPS y Operación):

- Gestión de fallas -> **`Fallos`**
- Gestión de configuración -> **`Config`**
- Gestión de consumo -> **`Account`**
- Gestión de desempeño -> **`Perf`**
- Gestión de seguridad -> **`Seguridad`**
- Centro de Operaciones de Red -> **`NOC`**
- Mesa de ayuda y tickets -> **`Soporte`**

---

## 5. Convenciones del Equipo

- **Enlaces:** Cada evidencia se enlaza desde el archivo `.md` que la usa, el mismo día que se sube al repositorio.
- **Commits del repositorio:** Se debe seguir el formato `<letra>: descripción breve` (por ejemplo: `F: agrega catálogo de casos de falla`).
- **Capturas:** Todas las capturas de pantalla deben mostrar la fecha y la hora visibles.
- **Secretos:** Queda estrictamente prohibido subir contraseñas, claves privadas ni archivos de configuración sin limpiar (sensitivos).
