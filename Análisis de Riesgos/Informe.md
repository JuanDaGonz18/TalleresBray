# Análisis de Riesgos – Arquitectura Empresarial
**Empresa:** Bray Controls Andina

---

## 1. Contexto General (AS-IS)
Bray Controls Andina cuenta con una arquitectura tecnológica basada principalmente en soluciones de **Microsoft**, incluyendo servicios en la nube (**Azure**), correo corporativo (**Outlook**) y almacenamiento centralizado gestionado por el corporativo en Houston (Estados Unidos).

El sistema principal utilizado es un **ERP (LN)**, complementado con herramientas como Excel para la gestión operativa diaria. La administración de infraestructura y seguridad es gestionada en gran medida por el equipo corporativo de TI, mientras que el soporte local es limitado y depende de terceros en caso necesario.

Se identificó una:
* Alta dependencia de procesos manuales.
* Uso recurrente de archivos externos (Excel).
* Baja formalización en políticas, procedimientos y controles de seguridad de la información.

---

## 2. Identificación de Riesgos
A partir del análisis de la arquitectura actual (AS-IS), entrevistas y evaluación de cumplimiento, se identificaron vulnerabilidades críticas en la centralización de datos y la falta de protocolos de seguridad robustos.

---

## 3. Matriz de Riesgos

| Riesgo | Causa | Impacto | Probabilidad | Dominio | Mitigación |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Fuga o pérdida de información** | Uso de Excel para manejo de datos críticos | Alto | Alta | Datos / Procesos | Centralizar la información en el ERP |
| **Accesos no autorizados** | No existe autenticación multifactor (MFA) | Alto | Alta | Seguridad | Implementar MFA |
| **Falta de trazabilidad** | Procesos manuales y herramientas no integradas | Alto | Alta | Procesos | Implementar tracking automatizado |
| **Interrupción de la operación** | Sin plan de continuidad del negocio documentado | Alto | Media | Infraestructura | Implementar plan de contingencia |
| **Manejo inadecuado de info.** | No existe clasificación de datos | Medio | Media | Datos | Definir esquema de clasificación |
| **Incidentes no gestionados** | Sin procedimiento formal de respuesta | Alto | Media | Seguridad | Definir plan de respuesta a incidentes |
| **Riesgos no gestionados** | No existe un SGSI implementado | Alto | Media | Gobierno TI | Implementar SGSI |
| **Acceso inconsistente** | Controles de acceso no unificados | Alto | Alta | Seguridad | Unificar control de accesos |
| **Errores operativos** | Alta dependencia de procesos manuales | Alto | Alta | Procesos | Automatizar procesos clave |
| **Dependencia de terceros** | Gestión de TI centralizada en Houston | Medio | Media | Infra / Gob | Definir acuerdos de servicio (SLA) |

---

## 4. Evaluación de Cumplimiento

| N° | Categoría | Criterio | Nivel | Evidencia | Recomendación |
| :-- | :--- | :--- | :--- | :--- | :--- |
| 1 | Datos Personales | Política de tratamiento de datos | ❌ | No se evidenció política formal | Definir política de tratamiento |
| 2 | Datos Personales | Consentimiento de uso de datos | ❌ | No hay mecanismos explícitos | Implementar consentimiento |
| 3 | Datos Personales | Control de acceso | ⚠️ | ERP controlado, pero Excel no | Centralizar accesos |
| 4 | Datos Personales | Clasificación de datos | ❌ | No existe clasificación formal | Definir clasificación de datos |
| 5 | Seguridad | Control por roles | ⚠️ | Solo en ERP | Unificar control de accesos |
| 6 | Seguridad | MFA | ❌ | No implementado | Implementar MFA |
| 7 | Seguridad | Gestión de usuarios | ⚠️ | No documentado | Formalizar proceso |
| 8 | Seguridad | Logs y auditoría | ❌ | No centralizados | Implementar auditoría |
| 9 | Seguridad | Protección de accesos | ⚠️ | Exposición en Excel | Reducir herramientas externas |
| 10 | Información | Integridad de datos | ❌ | Procesos manuales | Automatizar validación |
| 11 | Información | Disponibilidad | ⚠️ | Sin plan de contingencia | Implementar continuidad |
| 12 | Información | Protección datos sensibles | ⚠️ | Datos distribuidos | Centralizar |
| 13 | Operación | Trazabilidad | ❌ | Seguimiento manual | Automatizar tracking |
| 14 | Operación | Inventario | ⚠️ | Problemas de stock | Mejorar integración |
| 15 | Operación | Automatización | ❌ | Procesos manuales | Automatizar |
| 16 | Cumplimiento | Cumplimiento normativo | ⚠️ | Controles incompletos | Alinear normativa |
| 17 | Cumplimiento | SGSI | ⚠️ | No formal | Implementar SGSI |
| 18 | Cumplimiento | Gestión de riesgos | ❌ | No formal | Implementar matriz |
| 19 | Cumplimiento | Manejo de incidentes | ❌ | No definido | Definir plan |
| 20 | Cumplimiento | Fuga de información | ⚠️ | Uso de Excel y correo | Implementar DLP |

*Leyenda: ❌ Incumplimiento total | ⚠️ Cumplimiento parcial*

---

## 5. Análisis General de Riesgos
El análisis evidencia que la organización presenta riesgos significativos principalmente en los dominios de **procesos, datos y seguridad**. La alta dependencia de herramientas manuales como Excel, junto con la falta de controles formales, incrementa la probabilidad de errores operativos, pérdida de información y accesos no autorizados.

Adicionalmente, la ausencia de un **Sistema de Gestión de Seguridad de la Información (SGSI)** limita la capacidad de la organización para prevenir, detectar y responder ante incidentes. La dependencia del corporativo introduce riesgos adicionales relacionados con la autonomía operativa.

---

## 6. Relación con la Arquitectura TO-BE

La arquitectura objetivo (**TO-BE**) propuesta para **Bray Controls Andina** debe orientarse a resolver los riesgos identificados durante el análisis AS-IS, garantizando mayor resiliencia, integración, escalabilidad y continuidad operativa.

### 6.1 Centralización e integración de sistemas

Actualmente existe fragmentación entre el ERP LN, Dynamics 365, Order Track, archivos Excel y correos electrónicos, lo que genera reprocesos, duplicidad y pérdida de trazabilidad.

La arquitectura TO-BE debe contemplar:

- Integración nativa entre ERP, CRM y Order Track.
- Eliminación progresiva de procesos manuales soportados en Excel.
- Consolidación de información operativa, comercial y logística en una única plataforma integrada.
- Trazabilidad completa del ciclo de una orden sin depender de múltiples canales.

Esto mitigaría riesgos asociados a errores humanos, inconsistencias de datos y retrasos operativos.

### 6.2 Automatización de procesos críticos

Se identificó que procesos como la definición del reorder point continúan dependiendo de análisis manuales.

La arquitectura objetivo debe incluir:

- Automatización del cálculo de inventarios y puntos de reorden.
- Reglas automáticas de validación.
- Flujos digitales de aprobación.
- Alertas automáticas ante desviaciones.

Esto reduce la dependencia del conocimiento individual y mejora la eficiencia operativa.

### 6.3 Fortalecimiento de resiliencia tecnológica

Se reportó una interrupción total del sistema durante aproximadamente una semana debido a un incidente cibernético.

La arquitectura TO-BE debe incorporar:

- Planes formales de recuperación ante desastres.
- Redundancia de servicios críticos.
- Procedimientos documentados de continuidad operativa.
- Monitoreo proactivo de disponibilidad.

### 6.4 Gobierno y visibilidad tecnológica local

La sede local presenta alta dependencia del corporativo para soporte y decisiones tecnológicas.

La arquitectura objetivo debe fortalecer:

- Documentación formal de arquitectura.
- Definición clara de roles TI.
- Acuerdos de nivel de servicio (SLA).
- Procedimientos locales de escalamiento.

### 6.5 Seguridad y control de acceso

Aunque existen controles robustos como autenticación centralizada y restricción de dispositivos externos, no existe visibilidad local completa sobre incidentes.

La arquitectura TO-BE debe contemplar:

- Auditoría de accesos.
- Mayor observabilidad local.
- Reportes de incidentes compartidos.
- Formalización de lineamientos de seguridad.

---

## 7. Información Faltante o Incompleta

Durante el levantamiento de información se identificaron vacíos que limitan la precisión total del análisis.

### Infraestructura

No se obtuvo detalle técnico completo sobre:

- Arquitectura interna del ERP LN.
- Integraciones técnicas entre sistemas.
- Bases de datos utilizadas.
- Esquemas de respaldo corporativo.

### Gobierno TI

No existe visibilidad completa sobre:

- Estructura formal del área TI corporativa.
- SLA de soporte.
- Procedimientos de escalamiento.
- Responsables técnicos globales.

### Seguridad

Hace falta validar:

- Certificaciones formales como ISO 27001.
- Historial completo de incidentes.
- Auditorías internas o externas.
- Métricas de monitoreo.

### Procesos

Se requiere mayor formalización documental de:

- Flujos BPMN.
- Procesos de contingencia.
- Integraciones entre áreas.

### Evolución tecnológica

No existe claridad sobre:

- Roadmap corporativo.
- Estrategia futura de integración total.
- Proyectos de modernización.

---

## 8. Matriz de Riesgos

| Riesgo | Causa | Impacto | Probabilidad | Arquitectura afectada | Mitigación |
|--------|------|---------|-------------|----------------------|------------|
| Dependencia de Excel manuales | Procesos manuales | Alto | Alta | Procesos / Datos | Automatización |
| Fragmentación tecnológica | Sistemas no integrados | Alto | Alta | Aplicaciones | Integración mediante APIs |
| Interrupción del ERP | Dependencia del corporativo | Crítico | Media | Infraestructura | Redundancia y DRP |
| Baja visibilidad local | Centralización corporativa | Medio | Alta | Gobierno TI | Observabilidad local |
| Pérdida de trazabilidad | Uso de múltiples canales | Alto | Alta | Procesos | Plataforma unificada |
| Error en parametrización | Carga manual de datos | Medio | Media | Datos | Validaciones automáticas |

---

## 9. Caso práctico aplicado: Bray Controls Andina

### Contexto

Bray Controls Andina opera como filial regional para Colombia, Ecuador y Venezuela.

La organización depende del corporativo global para provisión tecnológica, seguridad y administración de plataformas empresariales.

Actualmente utiliza:

- ERP LN
- Dynamics 365
- Order Track
- Excel
- Correo corporativo

### Problemas identificados

- Fragmentación tecnológica.
- Dependencia de procesos manuales.
- Limitada trazabilidad.
- Dependencia del corporativo.
- Riesgos de continuidad operativa.

### Riesgos identificados

| Riesgo | Impacto | Arquitectura afectada |
|--------|---------|----------------------|
| Dependencia de Excel | Alto | Procesos / Datos |
| Caída del ERP | Crítico | Infraestructura |
| Dependencia del corporativo | Alto | Gobierno TI |
| Pérdida de trazabilidad | Alto | Procesos |
| Errores manuales | Medio-Alto | Datos |

### Propuesta TO-BE

Se propone una arquitectura basada en:

- Centralización de información.
- Integración completa entre sistemas.
- Automatización operativa.
- Observabilidad.
- Resiliencia tecnológica.
- Gobierno arquitectónico.

---

## 10. Recomendaciones para la entrega final

### El proyecto debe incluir

- Contexto organizacional.
- Arquitectura AS-IS.
- Riesgos identificados.
- Evidencias obtenidas.
- Matriz de riesgos.
- Mitigaciones propuestas.
- Arquitectura TO-BE.
- Justificación técnica.
- Conclusiones.

### Buenas prácticas

- Justificar técnicamente cada decisión.
- Relacionar riesgos con impacto de negocio.
- Priorizar riesgos críticos.
- Sustentar con evidencia real.
- Relacionar claramente AS-IS con TO-BE.

---

## Conclusión

El análisis de riesgos realizado sobre la arquitectura empresarial actual de **Bray Controls Andina** evidencia una organización con controles corporativos sólidos, pero con debilidades relevantes en integración, automatización, trazabilidad y autonomía tecnológica local.

Los principales riesgos identificados se concentran en:

- Dependencia de procesos manuales.
- Fragmentación entre plataformas.
- Alta dependencia del corporativo.
- Limitada visibilidad sobre incidentes.
- Riesgos operativos derivados de integración parcial.

La transición hacia una arquitectura TO-BE orientada a integración total, automatización, resiliencia y gobierno arquitectónico permitirá reducir estos riesgos y fortalecer la capacidad de crecimiento, continuidad operativa y transformación digital de la organización.

El caso demuestra que la arquitectura empresarial no debe verse únicamente como una estructura técnica, sino como una herramienta estratégica capaz de alinear tecnología y negocio, mejorar la eficiencia organizacional y preparar a la empresa para futuros escenarios de expansión y evolución digital.
