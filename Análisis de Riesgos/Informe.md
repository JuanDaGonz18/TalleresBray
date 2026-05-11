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
La arquitectura objetivo (TO-BE) debe enfocarse en mitigar los riesgos identificados mediante:

1.  **Centralización:** Consolidar la información en el ERP y eliminar silos en Excel.
2.  **Seguridad Robusta:** Implementación obligatoria de MFA y unificación de controles de acceso.
3.  **Automatización:** Digitalizar procesos críticos para reducir el error humano.
4.  **Gobierno:** Establecer formalmente un SGSI y políticas de manejo de datos.
5.  **Resiliencia:** Documentar y probar el plan de continuidad del negocio.

---

## 7. Información Faltante o Incompleta
Existen vacíos de información que deben ser validados para la precisión del análisis final:

* **Infraestructura:** Detalle técnico del ERP (arquitectura, base de datos, integraciones).
* **Roles:** Definición formal de roles y responsabilidades en el área de TI local.
* **Procesos:** Documentación técnica (BPMN o flujos formales).
* **Histórico:** Indicadores de incidentes previos o fallas recurrentes.
* **Corporativo:** Detalle de controles de seguridad de Houston y acuerdos de nivel de servicio (SLA).
* **Legal:** Evidencia documental de auditorías externas/internas realizadas.

---

## 8. Conclusión
El análisis de riesgos permite identificar debilidades estructurales en la arquitectura actual de **Bray Controls Andina**. La transición hacia una arquitectura TO-BE alineada con mejores prácticas de gobierno y seguridad permitirá no solo reducir riesgos operativos, sino también fortalecer la resiliencia y escalabilidad de la empresa frente a futuros retos digitales.