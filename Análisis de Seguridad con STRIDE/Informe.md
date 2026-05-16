# Informe Técnico – Análisis de Seguridad con STRIDE

**Equipo:** ARQTEAM-05  
**Integrantes:** Julián Barragán Pérez · Juan David González Rubio · Josue David Sarmiento  
**Cliente:** Bray Controls Andina Ltda  
**Fecha:** 2026

---

## 1. Introducción

En este informe se aplicó el modelo STRIDE al sistema operativo y tecnológico de Bray Controls Andina, empresa del sector industrial y comercial B2B.

El sistema analizado soporta el flujo completo desde la generación de la cotización hasta el despacho del producto, involucrando procesos de ventas, inventario, compras internacionales y facturación.

El objetivo es identificar riesgos de seguridad basados en evidencia real levantada en entrevistas con el equipo de la empresa, evaluar su impacto en la operación y proponer medidas de mitigación alineadas con la realidad del negocio.

> **Nota importante:** Este análisis incorpora un **incidente de seguridad real confirmado** por la empresa durante las entrevistas: un ataque cibernético ocurrido aproximadamente en 2022 que dejó todos los sistemas sin acceso durante una semana completa. Este hecho eleva varios riesgos de la categoría "teórico" a "históricamente confirmado".

---

## 2. Marco de análisis STRIDE

El modelo STRIDE clasifica las amenazas en seis categorías:

| Tipo | Descripción |
|------|------------|
| Spoofing | Suplantación de identidad |
| Tampering | Manipulación de datos |
| Repudiation | Negación de acciones |
| Information Disclosure | Exposición de información |
| Denial of Service | Interrupción del servicio |
| Elevation of Privilege | Escalamiento de privilegios |

---

## 3. Sistema analizado

El análisis se realizó sobre la arquitectura tecnológica de Bray Controls Andina, enfocado en el flujo operativo:

Cotización → Sales Order → Planeación → Compras → Recepción → Inventario → Despacho → Facturación

Componentes evaluados:

- **ERP LN** (Infor LN) — gestión de pedidos, compras e inventario; administrado desde Houston
- **Microsoft Dynamics 365** — CRM para cotizaciones y relación con clientes
- **Excel** — planeación manual, Reorder Point y seguimiento paralelo al ERP
- **Sistema de facturación electrónica** — separado del ERP LN; integración manual (no completada)
- **Microsoft Azure** — infraestructura en nube; backups cada 4-6 horas
- **Microsoft Outlook** — comunicación corporativa; canal principal entre áreas
- **Order Track** — seguimiento de órdenes (en implementación, kickoff 22 de mayo de 2025)

---

## 4. Metodología

Se siguieron los siguientes pasos:

1. Identificación de componentes críticos.
2. Revisión de información levantada en entrevistas con personal de Bray Controls Andina (Angélica — Operaciones; Felipe — Ventas internas; Julián Barragán — Director Técnico; Carlos Hernando Porras — Gerente General).
3. Aplicación del modelo STRIDE a cada componente.
4. Definición de escenarios reales de riesgo basados en la operación confirmada.
5. Evaluación de impacto y probabilidad.
6. Propuesta de controles y mitigaciones.

El resultado se documentó en la hoja **STRIDE_BrayAndina** del archivo Excel adjunto.

---

## 5. Resultados del análisis

### 5.1 Spoofing — Suplantación de identidad

**Componente:** ERP LN + Dynamics 365 + todos los aplicativos corporativos.

Todos los accesos a los sistemas de Bray Controls Andina están vinculados a la cuenta de correo corporativo Microsoft. Si un atacante obtiene acceso al correo de un empleado (por phishing, credential stuffing o reutilización de contraseñas), obtiene automáticamente acceso a LN, Dynamics 365, Order Track y demás aplicativos sin ninguna barrera adicional.

Este riesgo está agravado por el **incidente real de 2022**: el ataque cibernético que afectó a la empresa pudo haber tenido como vector inicial el compromiso de credenciales corporativas.

**Nivel de riesgo: Crítico**

---

### 5.2 Tampering — Manipulación de datos

**Componente 1: Excel de planeación (Reorder Point)**

El proceso de Reorder Point — que define cuándo y cuánto comprar — se gestiona en un archivo Excel propio del área de operaciones. No tiene controles de versión, auditoría ni restricción de edición. Cualquier modificación errónea o intencional en este archivo afecta directamente las órdenes de compra generadas por el LN.

Este riesgo es especialmente crítico dado que: (a) una sola persona toma estas decisiones, (b) el archivo no está integrado al ERP y (c) el proceso no está documentado.

**Componente 2: Facturación electrónica (proceso manual)**

La integración entre el ERP LN y el sistema de facturación electrónica no fue completada durante la última migración de versión del ERP. El proceso es actualmente manual. Esto introduce posibilidad de errores, omisiones y modificaciones no rastreables en los datos de facturación.

**Nivel de riesgo: Crítico**

---

### 5.3 Repudiation — Negación de acciones

**Componente:** Proceso de cotización y pedido (correos + Dynamics + LN)

La comunicación entre ventas externas, ventas internas y operaciones se realiza principalmente por correo electrónico. Los cambios en pedidos, urgencias de despacho, negociaciones de precio y decisiones operativas no quedan registrados de forma centralizada en el sistema. Angélica (Operaciones) confirmó: *"Cuando hay un pedido urgente sin stock, nos coordinamos por correo"*.

Si hay una disputa sobre qué se acordó, cuándo o quién lo autorizó, no existe un registro formal que lo respalde. Esto dificulta auditorías y genera riesgos legales con clientes.

**Nivel de riesgo: Alto**

---

### 5.4 Information Disclosure — Exposición de información

**Componente 1: Datos de clientes (Dynamics + correos + Excel)**

La información de clientes — precios pactados, condiciones comerciales, datos de contacto, historial de pedidos — está distribuida en tres lugares: Dynamics 365, correos de Outlook y archivos Excel. El uso de Excel sin controles de acceso expone información sensible a cualquier persona con acceso al archivo o al computador.

**Componente 2: IT Information Resource Policy (corporativo)**

Existe una política corporativa de seguridad de la información (IT Information Resource Policy, firmada por Craig Brown, CEO). Sin embargo, el personal local no puede acceder a ella — durante la entrevista, Angélica intentó descargarla y el sistema la bloqueó. El personal opera sin conocer formalmente los lineamientos de seguridad de la compañía, lo que aumenta el riesgo de manejo inadecuado de información.

**Nivel de riesgo: Alto**

---

### 5.5 Denial of Service — Interrupción del servicio

**Componente:** ERP LN + infraestructura corporativa

**Incidente real confirmado:** Bray Controls Andina sufrió un ataque cibernético (aproximadamente en 2022) que dejó todos los sistemas inaccesibles durante aproximadamente una semana. La empresa no pudo usar los computadores corporativos; el acceso quedó restringido a celulares y portátiles. La respuesta fue gestionada 100% desde el corporativo (Houston) vía Service Desk.

Las consecuencias operativas de ese incidente incluyeron:

- Imposibilidad de procesar pedidos, consultar inventario o emitir facturas.
- Dependencia total del corporativo para restablecer el acceso, sin participación ni capacidad de respuesta local.
- Implementación posterior de bloqueo total de puertos USB en todos los equipos como medida preventiva.

No existe ningún plan de contingencia local documentado. Si ocurre un nuevo incidente, la operación local volvería a paralizarse sin capacidad de respuesta autónoma.

**Nivel de riesgo: Crítico (históricamente confirmado)**

---

### 5.6 Elevation of Privilege — Escalamiento de privilegios

**Componente:** ERP LN + Dynamics 365

El acceso a los sistemas se gestiona por roles dentro de cada aplicativo. Sin embargo, no se evidenció un proceso formal de revisión periódica de permisos cuando un empleado cambia de rol o área. Si bien la revocación de acceso al salir de la empresa es automática (se desactiva la cuenta de correo corporativo), los cambios de rol intermedios pueden dejar permisos activos que ya no corresponden a las responsabilidades actuales del empleado.

**Nivel de riesgo: Alto**

---

## 6. Resumen de riesgos

| ID | Tipo | Componente | Nivel | Estado |
|----|------|-----------|-------|--------|
| S1 | Spoofing | ERP LN + Dynamics 365 | Crítico | Confirmado (incidente 2022) |
| S2 | Tampering | Excel Reorder Point | Crítico | Riesgo activo |
| S3 | Repudiation | Proceso cotización-pedido | Alto | Riesgo activo |
| S4 | Information Disclosure | Datos clientes dispersos | Alto | Riesgo activo |
| S5 | Denial of Service | ERP LN / infraestructura | Crítico | Históricamente confirmado |
| S6 | Elevation of Privilege | Roles en LN y Dynamics | Alto | Riesgo potencial |
| S7 | Tampering | Facturación electrónica manual | Alto | Riesgo activo |
| S8 | Information Disclosure | Política seguridad inaccesible | Alto | Riesgo activo |

---

## 7. Propuestas de mitigación

- Implementar **autenticación multifactor (MFA)** en todas las cuentas corporativas Microsoft — coordinación con Houston.
- **Documentar y probar un plan de contingencia local** que permita operar con capacidad mínima ante una caída del ERP.
- **Completar la integración** entre ERP LN y sistema de facturación electrónica, eliminando el proceso manual.
- **Migrar el proceso de Reorder Point al ERP LN** para eliminar la dependencia del archivo Excel y agregar trazabilidad.
- **Centralizar la información de clientes en Dynamics 365**, eliminando el uso de correos y Excel como repositorios paralelos.
- Gestionar con Houston el **acceso formal a la IT Information Resource Policy** para socialización local.
- Implementar **revisión periódica de roles activos** (mínimo semestral) en LN y Dynamics.
- Establecer un **protocolo formal de gestión de incidentes** con tiempos de respuesta y canales de escalamiento definidos.

---

## 8. Buenas prácticas de seguridad aplicables

Se recomienda adoptar, en coordinación con el corporativo:

- Modelo **Zero Trust** — verificar siempre, no solo en el perímetro.
- **Segmentación de accesos** por área y función, con revisión periódica.
- **Logs centralizados** de acciones en todos los sistemas.
- Actualización constante de software y parches de seguridad.
- Evaluaciones periódicas de vulnerabilidades.

> **Nota:** La empresa confirmó explícitamente que no maneja ni requiere certificación ISO 27001, ya que su negocio es la comercialización de válvulas y no la gestión de información como activo principal. Los controles de seguridad de la información son responsabilidad del corporativo Houston.

---

## 9. Conclusión

El análisis STRIDE sobre la operación real de Bray Controls Andina evidenció riesgos significativos, varios de ellos confirmados mediante el incidente histórico de 2022 y los procesos manuales actualmente en uso.

Los riesgos más críticos son la dependencia de un único canal de autenticación (correo corporativo) sin MFA, la gestión manual del Reorder Point en Excel, la falta de un plan de contingencia local y la ausencia de integración entre el ERP LN y la facturación electrónica.

La arquitectura TO-BE debe priorizar la integración de sistemas, la eliminación de procesos manuales paralelos y el establecimiento de un gobierno de IT local que permita a Bray Controls Andina responder de forma autónoma ante incidentes, sin depender totalmente del corporativo en Houston.

---

## Referencias

OWASP. *STRIDE Threat Model*.  
Microsoft. *Microsoft Security Best Practices*.  
Shostack, Adam. *Threat Modeling: Designing for Security*. Wiley, 2014.  
Ley 1581 de 2012 – Protección de Datos Personales en Colombia.
