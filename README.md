# Análisis de Arquitectura Empresarial — Bray Controls Andina

> *Este repositorio consolida toda la evidencia, entregables y hallazgos del proyecto de análisis y transformación de arquitectura empresarial realizado para Bray Controls Andina. Aquí encontrarás el trabajo completo: desde el diagnóstico inicial hasta la propuesta de arquitectura objetivo.*

---

## Descripción del Proyecto

**Bray Controls Andina Ltda** es una subsidiaria comercial de Bray International con operación en Colombia, Ecuador y Venezuela. Se dedica a la comercialización B2B de válvulas, actuadores y sistemas de automatización industrial, atendiendo sectores como petróleo y gas, energía, manufactura y tratamiento de agua. Cuenta con 45 empleados distribuidos en tres bodegas activas (Bogotá, Cali y Barranquilla) y su gestión tecnológica está centralizada en la casa matriz ubicada en Houston, Estados Unidos.

Este proyecto fue desarrollado con el propósito de realizar un **análisis integral de arquitectura empresarial** siguiendo el marco metodológico **TOGAF ADM**, identificando el estado actual de la organización (AS-IS), sus brechas críticas y proponiendo una hoja de ruta hacia un modelo más maduro, autónomo y alineado con las buenas prácticas del sector.

El análisis cubre las cuatro capas del modelo de arquitectura empresarial:

| Capa | Descripción |
|------|-------------|
| 🏢 **Negocio** | Procesos, estructura organizacional y operaciones comerciales |
| 🗂️ **Datos** | Gestión, retención, control y gobierno de la información |
| 💻 **Aplicaciones** | Herramientas tecnológicas, integraciones y dependencias |
| 🖥️ **Tecnología** | Infraestructura, nube, backups y soporte técnico |

---

##  Estructura del Repositorio

```
📁 bray-controls-andina-ae/
│
├── 📄 README.md
│
├── 📁 Ficha de Caracterización del Cliente/
│   └── 📄 Ficha_Caracterizacion_Cliente.md       ← Descripción de la empresa, objetivos,
│                                                     problemas, restricciones y contacto
│
├── 📁 Modelado de Proceso del Cliente con BPMN/
│   ├── 📄 Informe.md                             ← Análisis del proceso de cotización
│   │                                                y pedido industrial (AS-IS)
│   └── 📄 diagrama_bpmn.drawio                   ← Diagrama BPMN en Draw.io
│
├── 📁 Modelo de Información y Diagrama de Contexto/
│   ├── 📄 Informe.md                             ← Modelo ERD y flujos de información
│   └── 📄 ERD_BRY_Andina.drawio.png              ← Diagrama entidad-relación
│
├── 📁 Análisis de la Arquitectura de Infraestructura/
│   ├── 📄 Informe.md                             ← Análisis de infraestructura AS-IS
│   └── 📄 mapa.md                                ← Mapa lógico de sistemas e integraciones
│
├── 📁 Evaluación de Cumplimiento Normativo/
│   ├── 📄 Informe.md                             ← Diagnóstico de cumplimiento (Ley 1581,
│   │                                                ISO 9001, SARLAFT, Resolución 0312)
│   └── 📄 checklist.xlsx                         ← Checklist AS-IS con 20 criterios
│                                                    y hoja de incidentes históricos
│
└── 📁 Análisis de Seguridad con STRIDE/
    ├── 📄 Informe.md                             ← Informe STRIDE con incidente real (2022)
    └── 📄 StrideBrayAndina.xlsx                  ← Matriz de amenazas aplicada a Bray Andina
```

---

## Hallazgos Principales

Durante el análisis se identificaron problemáticas estructurales que atraviesan todas las capas de la arquitectura, sustentadas en evidencia real levantada en entrevistas con el equipo de la empresa:

### 1. Alta dependencia del corporativo en Houston

Toda la gestión de IT — accesos, configuraciones, cambios en sistemas, respuesta ante incidentes — depende del Service Desk corporativo. El soporte local lo realiza un contratista externo que también debe coordinarse con Houston para cualquier cambio. Esto quedó expuesto en el incidente de seguridad de 2022, donde la empresa estuvo **una semana sin acceso a sistemas** y no tuvo capacidad de respuesta autónoma.

### 2. Fragmentación tecnológica y ausencia de integración

La operación depende de cuatro sistemas que no están completamente integrados entre sí: **ERP LN**, **Dynamics 365**, **sistema de facturación electrónica** y **Excel**. La integración entre LN y la facturación electrónica no fue completada en la última migración. El seguimiento de órdenes se hace por correo y Excel. **Order Track** está en implementación con kickoff el 22 de mayo de 2025.

### 3. Procesos críticos manuales sin respaldo

El proceso de **Reorder Point** — que define cuándo y cuánto comprar — se gestiona en un archivo Excel por una sola persona, sin integración al LN ni documentación formal. El **SMI (Slow Moving Inventory)** asciende a aproximadamente **$4M USD (~30% del inventario total)**, sin política formal de disposición.

### 4. Gestión de seguridad sin visibilidad local

Existen controles de seguridad sólidos implementados por el corporativo (autenticación centralizada, bloqueo de USB tras el ataque de 2022, acceso restringido a equipos autorizados), pero el personal local no tiene visibilidad sobre ellos. La **IT Information Resource Policy** corporativa existe pero no es accesible localmente. No hay responsable formal de seguridad de la información a nivel Colombia.

### 5. Gobierno de datos débil a nivel local

Los datos de clientes viven en tres lugares distintos: Dynamics 365, correos de Outlook y archivos Excel. No existe fuente única de verdad. La política corporativa de tratamiento de datos personales existe pero no está documentada ni socializada localmente, generando brechas frente a la **Ley 1581 de 2012**.

---

## Propuesta de Transformación (TO-BE)

La arquitectura objetivo, inspirada en la necesidad expresada directamente por el equipo de operaciones — *"integrar todos los sistemas en uno solo donde yo pueda ver el proceso completo de una orden"* — se estructura en cinco ejes:

```
┌──────────────────────┬───────────────────────────────────────────┐
│ Integración          │ Un solo flujo: cotización → pedido →      │
│ de Sistemas          │ compra → bodega → despacho → factura      │
│                      │ sin correos ni Excel intermedios           │
├──────────────────────┼───────────────────────────────────────────┤
│ Automatización       │ Reorder Point en LN                       │
│ Operativa            │ Alertas automáticas de stock y SMI        │
│                      │ Flujos digitales de aprobación            │
├──────────────────────┼───────────────────────────────────────────┤
│ Resiliencia y        │ Plan de contingencia local documentado    │
│ Continuidad          │ Protocolo de incidentes con SLA Houston   │
│                      │ Capacidad de operación mínima offline     │
├──────────────────────┼───────────────────────────────────────────┤
│ Gobierno de TI       │ Roles locales de soporte IT definidos     │
│ Local                │ Proceso formal de escalamiento            │
│                      │ Documentación de arquitectura             │
├──────────────────────┼───────────────────────────────────────────┤
│ Seguridad y          │ MFA en cuentas corporativas               │
│ Gobierno de Datos    │ Centralización de datos en Dynamics 365   │
│                      │ Socialización local de política IT        │
│                      │ Cumplimiento Ley 1581 formalizado         │
└──────────────────────┴───────────────────────────────────────────┘
```

---

## 📋 Estado del Proyecto

| Fase | Estado |
|------|--------|
| ✅ Ficha de caracterización del cliente | Completado |
| ✅ Modelado de procesos AS-IS (BPMN) | Completado |
| ✅ Modelo de información y ERD | Completado |
| ✅ Análisis de arquitectura de infraestructura | Completado |
| ✅ Evaluación de cumplimiento normativo | Completado |
| ✅ Análisis de riesgos con STRIDE | Completado |
| ✅ Análisis de riesgos empresariales | Completado |
| 🔄 Formalización de arquitectura TO-BE | En progreso |
| 🔄 Definición de roadmap de transformación | En progreso |
| 🔄 Propuesta de gobierno de TI local | En progreso |

---

## Ecosistema Tecnológico Analizado

| Sistema | Tipo | Rol | Usuarios | Estado |
|---------|------|-----|----------|--------|
| **ERP LN** (Infor) | ERP corporativo | Pedidos, inventario, compras, despachos | 37 | Activo |
| **Microsoft Dynamics 365** | CRM | Cotizaciones y relación con clientes | ~22 | Activo |
| **Microsoft Azure** | Nube | Infraestructura y backups (cada 4-6 h) | — | Activo |
| **Microsoft Outlook** | Comunicación | Correo corporativo | 37 | Activo |
| **Sistema de facturación electrónica** | Facturación | Normativa colombiana | — | Activo — integración manual pendiente |
| **Excel** | Herramienta manual | Reorder Point, planeación, seguimiento | Múltiples | Activo — riesgo identificado |
| **Order Track** | Seguimiento | Trazabilidad operativa | 37 (previsto) | En implementación |

> **Conclusión clave:** La base tecnológica es sólida. Los desafíos no son tecnológicos, sino de **arquitectura, integración, gobierno y gestión**.

---

## Marco Normativo de Referencia

| Normativa / Framework | Aplicación en el proyecto |
|-----------------------|--------------------------|
| **Ley 1581 de 2012** | Protección de datos personales en Colombia — brecha identificada en formalización local |
| **ISO 9001** | Certificación activa de Bray Controls Andina — base de procesos de calidad |
| **Resolución 0312 de 2019** | Seguridad y salud en el trabajo — cumplimiento activo |
| **SARLAFT** | Prevención de lavado de activos — cumplimiento activo con verificación de terceros |
| **TOGAF ADM** | Marco metodológico del proyecto — estructura AS-IS / TO-BE |
| **COBIT** | Referencia para gobierno y gestión de TI |

> **Nota:** ISO 27001 fue evaluado y confirmado como no aplicable para Bray Controls Andina, dado que su negocio es la comercialización de productos industriales y no la gestión de información como activo principal. Los controles de seguridad de la información son responsabilidad del corporativo Houston.

---

## Equipo del Proyecto

Este análisis fue desarrollado como proyecto académico de **Arquitectura Empresarial** en la **Universidad de La Sabana**:

| Integrante | Rol |
|-----------|-----|
| Julián Andrés Barragán Pérez | ARQTEAM-05 |
| Juan David González Rubio | ARQTEAM-05 |
| Josue David Sarmiento Guarnizo | ARQTEAM-05 |

**Cliente:** Bray Controls Andina Ltda  
**Contacto:** Carlos Hernando Porras López — Gerente General · 316 4116484

---

## Nota Final

> *"No es un problema tecnológico, es un problema de arquitectura y gobierno."*
>
> Bray Controls Andina tiene las herramientas. Este proyecto define el **cómo usarlas mejor** — y el camino para hacerlo de forma autónoma, integrada y sostenible.

---

<div align="center">

**Proyecto de Arquitectura Empresarial · ARQTEAM-05 · Universidad de La Sabana · 2026**

</div>
