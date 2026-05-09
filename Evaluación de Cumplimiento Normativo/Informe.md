# Informe Técnico – Evaluación de Cumplimiento Normativo

**Equipo:** ARQTEAM-05  
**Integrantes:** Julián Barragán Pérez · Juan David González Rubio · Josue David Sarmiento  
**Cliente:** Bray Controls Andina Ltda  
**Fecha:** 2026

---

## 1. Introducción

El presente informe documenta el análisis de cumplimiento normativo realizado sobre el sistema operativo y tecnológico de Bray Controls Andina, empresa del sector industrial.

El objetivo fue evaluar el nivel de cumplimiento en aspectos de seguridad, operación, datos personales y gobierno organizacional, a partir de información levantada directamente en entrevistas con responsables técnicos y del negocio.

A diferencia de un enfoque teórico, este análisis se basa en evidencia real proporcionada por la organización, permitiendo identificar con mayor precisión fortalezas, brechas y riesgos.

---

## 2. Contexto organizacional y tecnológico

Bray Controls Andina opera bajo un modelo corporativo donde la gestión tecnológica está centralizada en la casa matriz ubicada en Houston (Estados Unidos).

### Características clave

- La gestión de IT y seguridad es responsabilidad del corporativo.
- Existe soporte técnico local limitado, a cargo de Julián David Rodríguez.
- Las decisiones tecnológicas no son completamente autónomas a nivel local.
- Se utilizan herramientas del ecosistema Microsoft.

### Infraestructura tecnológica

La empresa opera con dos sistemas principales claramente diferenciados en función y alcance:

**ERP LN (sistema central corporativo)**
- Gestión de pedidos (Sales Orders), inventario, compras (Purchase Orders) y despachos.
- Administrado desde Houston.
- Repositorio central de toda la operación logística y comercial.

**Microsoft Dynamics 365 (CRM)**
- Gestión de cotizaciones y relación con clientes.
- Jala información del cliente automáticamente para agilizar la elaboración de cotizaciones.
- Integrado con el flujo comercial: las cotizaciones en Dynamics se vinculan directamente a los pedidos registrados en LN.

Adicionalmente, la empresa utiliza:

- **Microsoft Azure** — infraestructura en nube para respaldo y disponibilidad de datos.
- **Microsoft Outlook** — comunicación corporativa y correo electrónico.
- **Excel** — seguimiento de planeación, órdenes y procesos complementarios (uso paralelo al ERP).
- **Sistema de facturación electrónica** — independiente del ERP LN, requerido por normativa colombiana.
- **Order Track** — aplicativo adicional para seguimiento de órdenes (en proceso de implementación).

### Distribución física

La empresa cuenta con tres bodegas activas en Colombia:

- **Bogotá** (sede principal — Tenjo, Cundinamarca)
- **Cali**
- **Barranquilla**

---

## 3. Metodología

El análisis se desarrolló mediante:

1. Entrevistas a actores clave:
   - Encargado técnico (Julián David Rodríguez — TI local)
   - Responsable operativo (Angélica — Operaciones)
   - Responsable comercial (Felipe — Ventas internas)
   - Gerente General (Carlos Hernando Porras López)

2. Revisión de procesos operativos y tecnológicos.

3. Construcción de checklist de cumplimiento por categorías.

4. Evaluación con niveles:
   - ✅ Cumple
   - ⚠️ Parcial
   - ❌ No cumple

5. Identificación de brechas y riesgos.

---

## 4. Modelo de evaluación

Se estructuró el análisis en cinco categorías:

- Seguridad de la información
- Protección de datos personales
- Arquitectura tecnológica
- Procesos y operación
- Cumplimiento y gobierno

---

## 5. Resultados del análisis

### 5.1 Seguridad de la información

La seguridad está fuertemente controlada por el corporativo:

- No se permite el uso de dispositivos externos (USB).
- Los accesos están restringidos y controlados a nivel de sistemas.
- La información está altamente protegida por lineamientos corporativos.

Sin embargo:

- No existe gestión visible ni documentada a nivel local.
- La documentación de controles no es accesible para la operación local.
- La empresa no maneja ISO 27001 como estándar formal (confirmado en entrevista).

**Conclusión:** Existe un alto nivel de seguridad operativa definido desde el corporativo, pero con baja visibilidad y control local. Los controles están implementados pero no son auditables desde Colombia.

---

### 5.2 Protección de datos personales

Se identificó que:

- Existe una **política corporativa de tratamiento de datos personales**, incluyendo manejo de datos biométricos bajo lineamientos específicos.
- Los clientes deben diligenciar un **formulario de conocimiento del cliente** al inicio de la relación comercial.
- El acceso a datos personales está restringido por áreas dentro de la organización.

Los datos de clientes se almacenan en:

- **ERP LN** (datos de pedidos, historial comercial)
- **Microsoft Dynamics 365** (datos de contacto y cotizaciones)

Sin embargo:

- La política de tratamiento de datos existe a nivel corporativo, pero **no está documentada formalmente a nivel local** ni es de fácil acceso para el personal colombiano.
- No se identificaron mecanismos explícitos para ejercer los derechos del titular (consulta, modificación, eliminación) conforme a la Ley 1581 de 2012.
- No existe un responsable designado localmente para la protección de datos personales.

**Conclusión:** Cumplimiento parcial. Existen bases sólidas (política corporativa, formulario de cliente, accesos restringidos), pero falta formalización local, accesibilidad de la política y mecanismos para derechos del titular conforme a la normativa colombiana.

---

### 5.3 Arquitectura tecnológica

Características principales:

- Infraestructura basada en Microsoft (Azure, Outlook, LN, Dynamics 365).
- Backups automáticos cada 4 a 6 horas hacia la nube (Azure).
- Información replicada desde dispositivos hacia la nube de forma continua.
- Mantenimiento periódico del sistema cada 2 semanas o cuando Microsoft lo requiera.

Gestión:

- Administración centralizada desde Houston (Estados Unidos).
- Soporte local a cargo de Julián David Rodríguez (encargado técnico).
- Para casos específicos que superen la capacidad local, se puede contratar soporte externo (limitado por los permisos de administración del grupo IT corporativo).

Aspectos positivos confirmados en entrevistas:

- No se han presentado pérdidas de información.
- Alta disponibilidad del sistema; no se han registrado casos de indisponibilidad.
- Las migraciones históricas han sido exitosas con errores mínimos.

**Conclusión:** Arquitectura sólida, estable y respaldada por infraestructura corporativa de alta disponibilidad. El principal riesgo es la dependencia total del corporativo para decisiones, cambios y soporte avanzado.

---

### 5.4 Procesos y operación

Se identificó que:

- Los procesos operativos funcionan correctamente en la práctica cotidiana.
- Se realizan reportes periódicos: **semanal** (ventas y estado de operación) y **mensual** (rendición de cuentas por capas y operativos).
- Existen revisiones constantes de desempeño e indicadores.

Sin embargo:

- La documentación no está centralizada; cada área gestiona su propia documentación de forma independiente.
- Los procesos no están estandarizados globalmente; el conocimiento operativo reside en las personas, no en documentos formales.
- El seguimiento de órdenes depende en gran parte de procesos manuales, llamadas internas y hojas de Excel paralelas al ERP.
- La integración entre áreas (ventas, operaciones, finanzas) es funcional pero informalmente coordinada.

**Conclusión:** Procesos funcionales con buen desempeño operativo, pero con baja formalización documental y alta dependencia de conocimiento tácito del personal.

---

### 5.5 Cumplimiento normativo y gobierno

La organización cumple con múltiples normativas:

- **ISO 9001** — Gestión de calidad (certificación activa).
- **Resolución 0312** — Seguridad y salud en el trabajo.
- **SARLAFT** — Sistema de administración de riesgo de lavado de activos y financiación del terrorismo (incluye verificación de terceros y análisis de riesgo).

Auditorías realizadas:

- Revisiones periódicas desde el corporativo (Houston).
- Auditorías externas (ISO, legales, aduanas, seguridad y salud en el trabajo).
- Rendición de cuentas mensual con indicadores de gestión.

Aspectos adicionales:

- Existe validación de terceros y evaluación de riesgos en el proceso SARLAFT.
- Los procesos de auditoría son gestionados por un encargado externo que verifica el cumplimiento de los requisitos.
- La documentación de cada proceso es responsabilidad del encargado del área correspondiente.

Sin embargo:

- No hay un **gobierno de IT local** definido; toda la gestión tecnológica depende del corporativo.
- No existe centralización de políticas ni un responsable local de cumplimiento tecnológico.

**Conclusión:** Alto cumplimiento normativo en áreas de calidad, seguridad laboral y prevención de riesgos financieros. La principal brecha está en el gobierno de IT, que opera de forma totalmente dependiente del exterior sin una estructura local definida.

---

## 6. Principales brechas identificadas

- Dependencia total del corporativo en IT, sin gobierno local definido.
- Política de tratamiento de datos existente a nivel corporativo pero no documentada ni accesible localmente.
- Ausencia de mecanismos formales para derechos del titular conforme a Ley 1581.
- Falta de centralización de documentación organizacional.
- Baja visibilidad local de los controles de seguridad implementados por el corporativo.
- Uso de Excel como herramienta paralela al ERP, generando riesgos de integridad y trazabilidad de datos.
- Falta de trazabilidad automática en el seguimiento de órdenes (dependencia de llamadas y seguimiento manual).

---

## 7. Fortalezas del sistema

- Infraestructura robusta basada en Microsoft con alta disponibilidad.
- Backups frecuentes y confiables (cada 4-6 horas).
- Sin historial reciente de pérdida de información ni incidentes críticos.
- Cumplimiento activo de múltiples normativas (ISO 9001, SARLAFT, Resolución 0312).
- Auditorías constantes internas y externas.
- Arquitectura de dos sistemas diferenciados (LN para operación, Dynamics para CRM) que separa responsabilidades.

---

## 8. Propuestas de mejora

- Definir un **gobierno de IT local** con roles y responsabilidades claras.
- **Documentar y socializar localmente** la política de tratamiento de datos personales.
- Implementar mecanismos para ejercer **derechos del titular** conforme a Ley 1581.
- Designar un **responsable local de protección de datos** (Data Protection Officer o equivalente).
- Centralizar la documentación organizacional en un repositorio único.
- Formalizar la gestión de accesos y roles en todas las herramientas (no solo en el ERP).
- Reducir la dependencia de Excel mediante integración de procesos en el ERP LN.
- Documentar el plan de contingencia y continuidad del negocio a nivel local.

---

## 9. Conclusión

El análisis evidencia que Bray Controls Andina cuenta con una base tecnológica sólida, segura y respaldada por el corporativo. La empresa cumple con normativas relevantes y opera con buen desempeño operativo.

No obstante, los principales desafíos no son tecnológicos sino estructurales y de gobierno:

- Dependencia total del corporativo en decisiones tecnológicas.
- Falta de autonomía y documentación local.
- Brechas en la formalización del cumplimiento de normativas de datos personales a nivel local.

El fortalecimiento del gobierno de IT local, la documentación centralizada y la formalización de procesos de protección de datos permitirá mejorar la eficiencia, trazabilidad, capacidad de respuesta y cumplimiento normativo de la organización.

---

## 10. Referencias

1. Ley 1581 de 2012 – Protección de Datos Personales en Colombia
2. Habeas Data – Marco constitucional colombiano
3. ISO 9001 – Gestión de calidad
4. Resolución 0312 de 2019 – Seguridad y salud en el trabajo
5. SARLAFT – Sistema de administración de riesgo de lavado de activos y financiación del terrorismo
6. TOGAF – The Open Group Architecture Framework
