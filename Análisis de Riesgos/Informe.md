# Análisis de Riesgos – Arquitectura Empresarial
**Empresa:** Bray Controls Andina Ltda  
**Equipo:** ARQTEAM-05  
**Integrantes:** Julián Barragán Pérez · Juan David González Rubio · Josue David Sarmiento  
**Fecha:** 2026

---

## 1. Contexto General (AS-IS)

Bray Controls Andina es una subsidiaria comercial de Bray International con operación en Colombia, Ecuador y Venezuela. Se dedica a la comercialización de válvulas, actuadores y sistemas de automatización industrial en el segmento B2B, atendiendo sectores como petróleo y gas, energía, manufactura y tratamiento de agua.

La empresa cuenta con 45 empleados distribuidos en tres bodegas activas: Bogotá (sede principal — Tenjo, Cundinamarca), Cali y Barranquilla.

Su arquitectura tecnológica está basada en soluciones de Microsoft administradas centralmente desde Houston (Estados Unidos):

| Sistema | Rol |
|---------|-----|
| ERP LN (Infor) | Sistema central: pedidos, inventario, compras y despachos |
| Microsoft Dynamics 365 | CRM: cotizaciones y relación con clientes |
| Microsoft Azure | Infraestructura en nube; backups cada 4-6 horas |
| Microsoft Outlook | Comunicación corporativa |
| Sistema de facturación electrónica | Requerido por normativa colombiana; integración con LN incompleta |
| Excel | Seguimiento manual de planeación, Reorder Point y control operativo |
| Order Track | Seguimiento de órdenes (en implementación; kickoff 22 de mayo de 2025) |

El soporte IT local es provisto por un contratista externo que atiende requerimientos físicos (configuración de equipos, impresoras) y debe coordinar con el Service Desk corporativo para cualquier cambio en sistemas o permisos. Julián David Rodríguez, quien inicialmente fue identificado como encargado de TI, ocupa el cargo de **Director Técnico** de la empresa y actúa como punto de contacto con el corporativo, pero no administra los sistemas.

Las principales características del estado actual que generan riesgos son:

- Alta dependencia de procesos manuales y archivos Excel paralelos al ERP.
- Fragmentación entre sistemas: LN, Dynamics 365, facturación electrónica y Order Track no están completamente integrados.
- Baja autonomía local en decisiones tecnológicas y respuesta ante incidentes.
- Baja formalización en políticas, procedimientos y controles de seguridad a nivel local.
- Un incidente de seguridad real confirmado: ataque cibernético (~2022) que paralizó la operación durante una semana completa.

---

## 2. Identificación de Riesgos

A partir del análisis de la arquitectura actual (AS-IS), entrevistas con personal clave de Bray Controls Andina y evaluación de cumplimiento normativo, se identificaron vulnerabilidades en seis dominios: negocio, procesos, datos, aplicaciones, infraestructura y gobierno de TI.

El análisis incorpora evidencia real obtenida en entrevistas con Angélica (Operaciones), Felipe (Ventas internas) y Carlos Hernando Porras López (Gerente General), lo que permite distinguir entre riesgos teóricos y riesgos **activos o confirmados**.

---

## 3. Matriz de Riesgos

| # | Riesgo | Causa | Impacto | Probabilidad | Dominio | Estado | Mitigación |
|---|--------|-------|---------|-------------|---------|--------|-----------|
| R1 | Paralización total de la operación por ataque cibernético | Dependencia total del corporativo para respuesta; sin plan local | Crítico | Media | Infraestructura / Seguridad | **CONFIRMADO** (incidente 2022, ~1 semana sin sistemas) | Documentar plan de contingencia local; establecer SLA con Houston |
| R2 | Fuga o pérdida de información crítica | Uso de Excel para datos de inventario, clientes y planeación sin controles | Alto | Alta | Datos / Procesos | Activo | Centralizar información en ERP LN y Dynamics 365 |
| R3 | Accesos no autorizados | Sin autenticación multifactor (MFA); acceso ligado solo al correo corporativo | Alto | Alta | Seguridad | Activo | Implementar MFA en coordinación con IT corporativo |
| R4 | Falta de trazabilidad de órdenes | Coordinación por correo; seguimiento manual; Order Track aún no operativo | Alto | Alta | Procesos | Activo | Activar Order Track; formalizar registro de cambios en LN |
| R5 | Error en planeación de compras por proceso manual de Reorder Point | Una sola persona define y carga el Reorder Point en Excel; sin integración al LN | Alto | Media | Datos / Procesos | Activo | Migrar Reorder Point al LN; documentar el proceso |
| R6 | Error o manipulación en facturación | Integración entre LN y sistema de facturación electrónica no completada; proceso manual | Alto | Alta | Aplicaciones / Datos | Activo | Completar integración LN → facturación electrónica |
| R7 | Capital inmovilizado por SMI (~$4M USD) | Sin política formal de disposición de inventario de lento movimiento | Alto | Ya ocurrido | Operación / Negocio | Activo | Definir política formal de SMI con criterios y responsables |
| R8 | Incidentes sin gestión local | Sin procedimiento formal de respuesta; todo depende del corporativo | Alto | Media | Seguridad / Gobierno | Activo | Definir protocolo local de gestión de incidentes |
| R9 | Información de clientes inconsistente | Datos distribuidos en Dynamics, correos y Excel sin fuente única de verdad | Alto | Alta | Datos | Activo | Centralizar en Dynamics 365; eliminar Excel como repositorio |
| R10 | Riesgo político y sectorial | Dependencia del sector petróleo/gas/energía; decisiones gubernamentales afectan la demanda directamente | Crítico | Alta | Negocio | Confirmado (negocio con Israel bloqueado por decisión política) | Diversificar sectores de cliente; monitorear entorno regulatorio |
| R11 | Dependencia de persona única en inventario | Angélica es la única responsable de calcular y cargar el Reorder Point | Alto | Media | Procesos / Gobierno | Activo | Documentar el proceso; capacitar un segundo responsable |
| R12 | Acceso inconsistente a herramientas paralelas | Control de roles en LN y Dynamics, pero sin control en Excel y correos | Medio | Alta | Seguridad | Activo | Unificar control de accesos; reducir herramientas externas |
| R13 | Política de seguridad inaccesible localmente | La IT Information Resource Policy existe pero el sistema bloquea su descarga al personal local | Medio | Alta | Gobierno / Seguridad | Activo | Gestionar acceso formal con Houston; socializar localmente |
| R14 | Sin clasificación formal de datos | No existe esquema de clasificación de información sensible | Medio | Media | Datos | Activo | Definir esquema de clasificación alineado con política corporativa |
| R15 | Escalamiento de privilegios por roles no revisados | Sin proceso formal de revisión periódica cuando un empleado cambia de rol | Medio | Media | Seguridad | Potencial | Implementar revisión semestral de roles activos |

---

## 4. Evaluación de Cumplimiento

| N° | Categoría | Criterio | Nivel | Evidencia | Recomendación |
|:---|:----------|:---------|:------|:----------|:--------------|
| 1 | Datos Personales | Política de tratamiento de datos | ⚠️ | Existe política corporativa (IT Information Resource Policy) pero no está documentada ni accesible formalmente a nivel local en Colombia | Gestionar acceso y socializar localmente; designar responsable local de protección de datos |
| 2 | Datos Personales | Consentimiento explícito de uso de datos | ❌ | El formulario de conocimiento del cliente recoge información básica, pero no incluye cláusula de consentimiento conforme a Ley 1581 | Incorporar consentimiento informado en el formulario de conocimiento del cliente |
| 3 | Datos Personales | Control de acceso a datos personales | ⚠️ | ERP LN y Dynamics 365 tienen control, pero Excel y correos no tienen restricciones | Centralizar accesos y eliminar uso de Excel como repositorio de datos de clientes |
| 4 | Datos Personales | Clasificación de datos | ❌ | No existe esquema formal de clasificación de la información | Definir esquema de clasificación de datos en coordinación con corporativo |
| 5 | Seguridad | Control de acceso basado en roles | ⚠️ | Existe en LN y Dynamics; sin control en herramientas paralelas (Excel, correo) | Implementar control de acceso unificado en todas las herramientas |
| 6 | Seguridad | Autenticación segura (MFA) | ❌ | No se evidenció uso de autenticación multifactor; acceso ligado solo a correo corporativo | Implementar MFA en coordinación con IT corporativo (Houston) |
| 7 | Seguridad | Gestión de usuarios (altas y bajas) | ⚠️ | La baja está automatizada (se desactiva el correo); los cambios de rol no tienen proceso formal documentado | Documentar formalmente el proceso de baja y cambio de rol, con tiempos máximos de respuesta |
| 8 | Seguridad | Logs y auditoría centralizados | ❌ | No existe trazabilidad completa fuera del ERP; procesos en correo y Excel no son auditables | Implementar auditoría centralizada y logs de acciones críticas |
| 9 | Seguridad | Protección contra accesos no autorizados | ⚠️ | Acceso restringido a equipos corporativos autorizados; puertos USB bloqueados tras el ataque de 2022. Persiste exposición en Excel | Reducir herramientas externas; implementar DLP |
| 10 | Información | Integridad de datos | ❌ | Procesos manuales y uso de Excel afectan calidad; duplicidad de registros de producto confirmada (aunque en baja proporción) | Automatizar validación de datos; migrar procesos críticos al ERP LN |
| 11 | Información | Disponibilidad del sistema | ⚠️ | Se registró un ataque cibernético que interrumpió el servicio durante ~1 semana. Sin plan de contingencia local documentado | Documentar plan de continuidad del negocio a nivel local |
| 12 | Información | Protección de información sensible | ⚠️ | Datos de clientes distribuidos en Dynamics, correos y Excel sin fuente única de verdad | Centralizar almacenamiento de información de clientes en Dynamics 365 |
| 13 | Operación | Trazabilidad de órdenes | ❌ | Seguimiento manual por correo; Order Track aún en implementación (kickoff 22 de mayo) | Activar Order Track; establecer protocolo de registro en LN para cualquier cambio en pedidos |
| 14 | Operación | Gestión de inventario | ⚠️ | SMI de ~$4M USD (~30% del inventario total); Reorder Point manual en Excel sin integración al LN | Migrar Reorder Point al LN; definir política formal de disposición de SMI |
| 15 | Operación | Automatización de procesos | ❌ | Alta dependencia de procesos manuales en planeación, seguimiento y facturación | Automatizar flujo operativo; completar integración LN → facturación electrónica |
| 16 | Cumplimiento | Cumplimiento normativo general | ⚠️ | ISO 9001 activo; SARLAFT; Resolución 0312. Cumplimiento de Ley 1581 parcial a nivel local | Formalizar cumplimiento de Ley 1581 a nivel local |
| 17 | Cumplimiento | Sistema de Gestión de Seguridad (SGSI) | ⚠️ | Controles corporativos robustos pero no visibles ni auditables localmente. ISO 27001 no aplica (confirmado en entrevista) | Documentar y socializar los controles corporativos existentes a nivel local |
| 18 | Cumplimiento | Gestión de riesgos de seguridad | ❌ | No existe proceso formal local de gestión de riesgos de seguridad | Implementar matriz de riesgos y revisión periódica |
| 19 | Cumplimiento | Manejo de incidentes de seguridad | ❌ | Ataque cibernético de 2022 gestionado 100% por corporativo sin protocolo local documentado | Definir protocolo local de respuesta a incidentes con escalamiento a Houston |
| 20 | Cumplimiento | Protección contra fuga de información | ⚠️ | Uso de Excel y correos incrementa el riesgo; puertos USB bloqueados; política corporativa inaccesible localmente | Implementar DLP; socializar localmente la política de seguridad corporativa |

*Leyenda: ✅ Cumple · ⚠️ Cumplimiento parcial · ❌ Incumplimiento*

---

## 5. Análisis por Dominio

### 5.1 Negocio

El mayor riesgo estratégico identificado es la **dependencia sectorial**: Bray Controls Andina vende exclusivamente a sectores de petróleo, gas y energía. Decisiones gubernamentales que desincentiven la exploración o tensiones diplomáticas pueden afectar directamente la cartera de clientes. Este riesgo fue confirmado con un caso real: un negocio con Israel fue bloqueado por decisiones políticas del gobierno colombiano.

Adicionalmente, la empresa no cuenta con un responsable formal de IT a nivel local, lo que limita la capacidad de respuesta ante fallas tecnológicas que afecten la operación comercial.

### 5.2 Procesos

Los procesos operativos son funcionales, pero presentan alta dependencia de conocimiento tácito de personas clave. El proceso de Reorder Point es el caso más crítico: está centralizado en una sola persona (Angélica, Operaciones), se ejecuta en Excel sin integración al LN, y no está documentado. Si esa persona no está disponible, la planeación de compras se detiene.

La coordinación entre áreas (ventas, operaciones, finanzas) se realiza principalmente por correo electrónico, sin registro formal en ningún sistema.

### 5.3 Datos

La información operativa y comercial de la empresa vive en múltiples lugares: ERP LN, Dynamics 365, Excel y correos de Outlook. No existe una fuente única de verdad. Esto genera riesgo de inconsistencias (confirmado: pueden existir duplicidades de número de parte en LN y Excel), pérdida de contexto histórico y exposición de datos sensibles como precios y condiciones comerciales.

El SMI (~$4M USD, ~30% del inventario total) representa un riesgo financiero activo derivado de la falta de una política formal de disposición de inventario obsoleto o de lento movimiento.

### 5.4 Aplicaciones

La fragmentación tecnológica es el problema central en este dominio. La propia coordinadora de operaciones lo describió como *"pañitos de agua tibia"*: LN, Dynamics 365, Order Track, Excel y el sistema de facturación electrónica no están completamente integrados entre sí.

La integración entre LN y la facturación electrónica no fue completada durante la última migración de versión del ERP, por lo que el proceso de facturación sigue siendo manual. Order Track tiene su kickoff el 22 de mayo de 2025 y aún no está operativo.

### 5.5 Infraestructura

La infraestructura es sólida: Azure con backups cada 4-6 horas, alta disponibilidad histórica y migraciones exitosas. Sin embargo, el **incidente real de 2022** demostró que esta solidez no garantiza continuidad operativa local. Durante el ataque cibernético, la empresa estuvo sin acceso a sistemas por una semana completa, sin capacidad de respuesta autónoma y dependiendo 100% del corporativo.

Como consecuencia del ataque, el corporativo bloqueó todos los puertos USB en equipos corporativos, lo que es un control positivo pero implementado reactivamente.

### 5.6 Gobierno de TI

No existe gobierno de TI local. Las decisiones tecnológicas, los accesos a sistemas, los cambios de configuración y la respuesta ante incidentes dependen del Service Desk de Houston. El contratista local solo puede atender requerimientos físicos básicos y también debe coordinarse con Houston para cualquier cambio en sistemas.

Esto genera un riesgo estructural: ante cualquier problema tecnológico, la operación local queda subordinada a los tiempos de respuesta del corporativo, sin mecanismos de escalamiento formalmente documentados.

---

## 6. Relación con la Arquitectura TO-BE

La arquitectura objetivo debe resolver los riesgos identificados, priorizando los de mayor impacto. Angélica (Operaciones) resumió la necesidad del TO-BE en una sola frase durante la entrevista:

> *"Me encantaría poder tener algo donde yo tenga todo en el mismo sistema. Eso nos hace muy poco eficientes. Tanto correo para dar una vaina de una orden. Lo que cambiaría es integrarlo: que yo pueda ver todo el proceso de una misma orden ahí mismo."*

Con base en los riesgos identificados, la arquitectura TO-BE debe estructurarse en cinco ejes:

### 6.1 Integración de sistemas

Resolver la fragmentación entre LN, Dynamics 365, Order Track y facturación electrónica mediante integración nativa o vía APIs. Objetivo: que el ciclo completo de una orden (cotización → pedido → compra → bodega → despacho → factura) sea visible en un solo sistema, sin depender de correos ni Excel intermedios.

Riesgos que mitiga: R4, R6, R9.

### 6.2 Automatización de procesos críticos

Migrar el proceso de Reorder Point al ERP LN y automatizar las reglas de reposición de inventario. Establecer alertas automáticas de stockout y SMI. Digitalizar flujos de aprobación de ajustes de inventario.

Riesgos que mitiga: R5, R7, R11.

### 6.3 Resiliencia y continuidad operativa

Documentar un plan de contingencia local que establezca qué operaciones pueden ejecutarse durante una interrupción del ERP, cómo comunicarse con Houston, cuáles son los tiempos máximos de respuesta esperados y quién es responsable de cada acción.

Riesgos que mitiga: R1, R8.

### 6.4 Gobierno de TI local

Definir formalmente los roles de soporte TI local, los procedimientos de escalamiento al corporativo y los acuerdos de nivel de servicio (SLA) con Houston. Documentar la arquitectura tecnológica actual y establecer un proceso de gestión de cambios.

Riesgos que mitiga: R8, R13, R15.

### 6.5 Seguridad y gobierno de datos

Implementar MFA en todas las cuentas corporativas (en coordinación con Houston). Centralizar los datos de clientes en Dynamics 365 y eliminar el uso de Excel como repositorio paralelo. Socializar localmente la IT Information Resource Policy corporativa. Definir un esquema de clasificación de datos.

Riesgos que mitiga: R2, R3, R9, R12, R13, R14.

---

## 7. Información Faltante o Incompleta

Durante el levantamiento de información se identificaron vacíos que deben complementarse para mayor precisión del análisis:

- **Finanzas:** Detalle del proceso manual de facturación electrónica y número de usuarios del sistema — requiere entrevista con "H" (responsable de finanzas).
- **Corporativo:** Detalle de los SLAs de respuesta del Service Desk de Houston, estructura del equipo IT corporativo y controles de seguridad específicos implementados tras el ataque de 2022.
- **Expansión:** Información sobre el modelo tecnológico de Bray Ecuador ya constituida — qué sistemas usa, si comparte el LN con Colombia y cómo se gestiona el inventario para esa operación.
- **Roles IT:** Formalizar en un documento el alcance del contratista local, el rol de Julián David Rodríguez como Director Técnico y el proceso de escalamiento a Houston.

---

## 8. Conclusión

El análisis de riesgos sobre la arquitectura empresarial de Bray Controls Andina evidencia una organización con una base tecnológica corporativa sólida, pero con debilidades estructurales relevantes en integración, automatización, trazabilidad y gobierno tecnológico local.

El principal hallazgo del análisis no es tecnológico: es de arquitectura y gobierno. La empresa tiene las herramientas —LN, Dynamics 365, Azure— pero opera con procesos manuales, sistemas desintegrados y sin capacidad de respuesta autónoma ante incidentes.

Los riesgos más críticos confirmados son:

- El ataque cibernético de 2022 que paralizó la operación durante una semana, sin protocolo local de respuesta.
- La gestión manual del Reorder Point por una sola persona, sin respaldo ni documentación.
- La fragmentación tecnológica que impide ver el ciclo completo de una orden en un solo sistema.
- El riesgo político y sectorial derivado de la concentración de clientes en el sector extractivo.

La transición hacia la arquitectura TO-BE debe priorizar la integración de sistemas, la documentación de procesos críticos, el establecimiento de un gobierno de TI local y la construcción de un plan de contingencia que permita a Bray Controls Andina operar con autonomía ante cualquier interrupción del corporativo.

El caso demuestra que la arquitectura empresarial no es únicamente una estructura técnica: es la herramienta que determina la resiliencia, la eficiencia y la capacidad de crecimiento de la organización.

---

## Referencias

1. Ley 1581 de 2012 – Protección de Datos Personales en Colombia
2. ISO 9001 – Gestión de Calidad
3. Resolución 0312 de 2019 – Seguridad y Salud en el Trabajo
4. SARLAFT – Sistema de Administración de Riesgo de Lavado de Activos y Financiación del Terrorismo
5. TOGAF – The Open Group Architecture Framework
6. COBIT – Gobierno y Gestión de TI
7. Shostack, Adam. *Threat Modeling: Designing for Security*. Wiley, 2014.
8. The Open Group. *TOGAF Standard, Version 9.2*. 2018.
