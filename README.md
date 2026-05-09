# Análisis de Arquitectura Empresarial — Bray Controls Andina

> *Este repositorio consolida toda la evidencia, entregables y hallazgos del proyecto de análisis y transformación de arquitectura empresarial realizado para Bray Controls Andina. Aquí encontrarás el trabajo completo: desde el diagnóstico inicial hasta la propuesta de arquitectura objetivo.*

---

## Descripción del Proyecto

**Bray Controls Andina** es una empresa regional dedicada a la comercialización de soluciones industriales —válvulas y automatización— que forma parte de una estructura corporativa internacional con sede en Estados Unidos.

Este proyecto fue desarrollado con el propósito de realizar un **análisis integral de arquitectura empresarial**, identificando el estado actual de la organización, sus brechas críticas y proponiendo una hoja de ruta hacia un modelo más maduro, autónomo y alineado con las buenas prácticas del sector.

El análisis cubre las cuatro capas del modelo de arquitectura empresarial:

| Capa | Descripción |
|------|-------------|
|  **Negocio** | Procesos, estructura organizacional y operaciones comerciales |
|  **Datos** | Gestión, retención, control y gobierno de la información |
|  **Aplicaciones** | Herramientas tecnológicas, integraciones y dependencias |
|  **Tecnología** | Infraestructura, nube, backups y soporte técnico |

---

##  Estructura del Repositorio

```
📁 bray-controls-andina-ae/
│
├── 📄 README.md                        ← Este archivo
│
├── 📁 01_contexto/
│   ├── contexto_organizacional.md      ← Descripción de la empresa y su entorno corporativo
│   └── alcance_y_objetivos.md          ← Delimitación del proyecto
│
├── 📁 02_as-is/
│   ├── arquitectura_negocio.md         ← Procesos actuales y estructura organizacional
│   ├── arquitectura_datos.md           ← Estado actual de la gestión de datos
│   ├── arquitectura_aplicaciones.md    ← Inventario y análisis de herramientas (Dynamics, Azure, etc.)
│   ├── arquitectura_tecnologia.md      ← Infraestructura, nube y soporte
│   └── seguridad_y_cumplimiento.md     ← Controles actuales y cumplimiento normativo (Ley 1581)
│
├── 📁 03_analisis_brechas/
│   ├── gap_analysis.xlsx               ← Matriz de brechas AS-IS vs buenas prácticas
│   └── resumen_brechas.md              ← Síntesis de los hallazgos críticos
│
├── 📁 04_to-be/
│   ├── arquitectura_objetivo.md        ← Propuesta de arquitectura futura
│   ├── gobierno_de_datos.md            ← Políticas y lineamientos propuestos
│   └── seguridad_estructurada.md       ← Modelo de seguridad y gestión de accesos
│
├── 📁 05_roadmap/
│   └── roadmap_transformacion.md       ← Hoja de ruta priorizada de implementación
│
└── 📁 06_anexos/
    ├── entrevistas/                    ← Notas y hallazgos de sesiones con stakeholders
    └── referencias/                   ← Normativas, frameworks y fuentes consultadas
```

---

##  Hallazgos Principales

Durante el análisis se identificaron **cinco problemáticas estructurales** que atraviesan todas las capas de la arquitectura:

### 1.  Alta dependencia del corporativo
El área de IT opera bajo lineamientos externos, con baja autonomía para tomar decisiones tecnológicas a nivel local. Las necesidades regionales no siempre están alineadas con las prioridades globales.

### 2.  Ausencia de documentación centralizada
La información está dispersa entre diferentes personas, herramientas y áreas. No existe un repositorio único que centralice procesos, políticas ni decisiones técnicas.

### 3.  Gestión de accesos sin estructura formal
No se evidencia un proceso claro para la asignación, revisión y revocación de accesos. Esto representa un riesgo tanto operativo como de cumplimiento normativo.

### 4.  Gobierno de datos débil
No existen políticas formales de retención, eliminación ni control de datos personales, lo que genera riesgos frente a la **Ley 1581 de protección de datos** en Colombia.

### 5.  Procesos no formalizados
Los procesos operan por inercia organizacional, pero no están documentados ni estandarizados, lo que dificulta su mejora, auditoría y transferencia de conocimiento.

---

##  Propuesta de Transformación (TO-BE)

La arquitectura objetivo se estructura en torno a cinco ejes de mejora:

```
┌─────────────────────────────────────────────────────┐
│              ARQUITECTURA OBJETIVO                  │
├──────────────────┬──────────────────────────────────┤
│ Autonomía Local  │ Roles internos de IT definidos   │
│                  │ Reducción de dependencia externa  │
├──────────────────┼──────────────────────────────────┤
│ Gobierno de Datos│ Políticas de retención           │
│                  │ Control de acceso estructurado   │
│                  │ Cumplimiento Ley 1581            │
├──────────────────┼──────────────────────────────────┤
│ Documentación    │ Repositorio centralizado         │
│ Centralizada     │ Estándares documentales          │
├──────────────────┼──────────────────────────────────┤
│ Seguridad        │ Gestión formal de accesos        │
│ Estructurada     │ Protocolo de incidentes          │
│                  │ Auditoría periódica              │
├──────────────────┼──────────────────────────────────┤
│ Formalización    │ Documentación de procesos        │
│ de Procesos      │ Estandarización operativa        │
└──────────────────┴──────────────────────────────────┘
```

---

##  Estado del Proyecto

| Fase | Estado |
|------|--------|
| ✅ Análisis del contexto empresarial | Completado |
| ✅ Identificación de sistemas y tecnología | Completado |
| ✅ Levantamiento de procesos generales | Completado |
| ✅ Detección de problemas clave | Completado |
| ✅ Análisis de brechas (GAP) | Completado |
| 🔄 Formalización de arquitectura TO-BE | En progreso |
| 🔄 Definición de roadmap | En progreso |
| 🔄 Propuesta de gobierno | En progreso |

---

##  Tecnología Analizada

El ecosistema tecnológico actual de Bray Controls Andina está basado principalmente en soluciones **Microsoft**:

- **Microsoft Dynamics 365** — Gestión empresarial (ERP/CRM)
- **Microsoft Outlook** — Comunicación corporativa
- **Microsoft Azure** — Infraestructura en nube
- Backups automáticos con frecuencia de **4 a 6 horas**

> **Conclusión clave:** La base tecnológica es sólida. Los desafíos no son tecnológicos, sino de **arquitectura, gobierno y gestión**.

---

##  Marco Normativo de Referencia

| Normativa / Framework | Aplicación |
|-----------------------|------------|
| **Ley 1581 de 2012** | Protección de datos personales en Colombia |
| **TOGAF** | Marco de referencia para arquitectura empresarial |
| **ISO 27001** | Gestión de seguridad de la información |
| **COBIT** | Gobierno y gestión de TI |

---

##  Equipo del Proyecto

Este análisis fue desarrollado como proyecto académico/profesional de arquitectura empresarial para **Bray Controls Andina** por Juan David González Rubio, Julian Andres Barragán Perez y Josue David Sarmiento Guarnizo, con el objetivo de entregar recomendaciones accionables y una visión estructurada del camino a seguir.

---

