# Informe Técnico – Análisis de Seguridad con STRIDE

## 1. Introducción

En este trabajo se aplicó el modelo STRIDE al sistema operativo y tecnológico de **Bray Andina**, empresa del sector logístico y comercial. 

El sistema analizado soporta el flujo desde la generación de la orden de venta (Sales Order) hasta el despacho del producto, involucrando procesos de inventario, compras y distribución.

El objetivo es identificar riesgos de seguridad, evaluar su impacto en la operación y proponer medidas de mitigación alineadas con la realidad del negocio.

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

Este marco permite analizar de forma estructurada los riesgos en cada componente del sistema.

---

## 3. Sistema analizado

El análisis se realizó sobre el sistema de Bray Andina, enfocado en el flujo operativo:

Sales Order → Planeación → Compras → Recepción → Inventario → Despacho

Componentes evaluados:

- ERP LN (gestión de órdenes, compras e inventario)
- Dynamics 365 (cotizaciones)
- Excel y herramientas manuales de seguimiento
- Sistema de bodega (warehouse)
- Integraciones con subsidiarias y proveedores internacionales

Estos componentes son críticos porque soportan la operación logística y el cumplimiento de pedidos a clientes.


---

## 4. Metodología

Se siguieron los siguientes pasos:

1. Identificación de componentes críticos.
2. Aplicación del modelo STRIDE a cada componente.
3. Definición de posibles escenarios de ataque.
4. Evaluación de impacto y probabilidad.
5. Propuesta de controles y mitigaciones.

El resultado se documentó en una tabla STRIDE en Excel.

---

## 5. Resultados del análisis

### 5.1 Spoofing (Suplantación de identidad)

Existe riesgo de acceso no autorizado si un atacante obtiene credenciales de usuarios del sistema (por ejemplo, del ERP o herramientas como Dynamics 365).

Esto podría permitir modificar órdenes o acceder a información sensible.

---

### 5.2 Tampering (Manipulación de datos)

Se identificó que varios procesos dependen de Excel y ajustes manuales, lo que permite modificaciones no controladas en fechas de entrega, asignación de inventario y seguimiento de órdenes incompletas.

Esto es especialmente crítico en escenarios donde existen pedidos incompletos o compras internacionales con tiempos de reposición de hasta 4–5 meses, lo que incrementa el riesgo de inconsistencias en la información operativa.


---

### 5.3 Repudiation (Negación de acciones)

No todos los procesos tienen trazabilidad clara. Algunas decisiones operativas (como cambios en órdenes o inventario) no quedan completamente registradas.

Esto dificulta auditorías y control de responsabilidades.

---

### 5.4 Information Disclosure (Exposición de información)

El uso de múltiples herramientas (Excel, correos, sistemas paralelos) aumenta el riesgo de fuga de información como:

- Datos de clientes
- Precios
- Inventario

Especialmente si no hay controles de acceso adecuados.

---

### 5.5 Denial of Service (Interrupción del servicio)

El sistema depende fuertemente del ERP y de la coordinación entre áreas. Una caída del sistema o saturación podría detener:

- Procesamiento de órdenes
- Movimientos de inventario
- Despachos

Esto impacta directamente la operación del negocio.

---

### 5.6 Elevation of Privilege (Escalamiento de privilegios)

Un usuario con permisos limitados podría acceder a funciones críticas si no hay una correcta gestión de roles.

Esto puede permitir acciones como:

- Modificar órdenes
- Acceder a información sensible
- Alterar inventario

---

## 6. Propuestas de mitigación

Se proponen las siguientes medidas:

- Implementar **autenticación multifactor (MFA)**.
- Mejorar la **gestión de roles y permisos** (principio de mínimo privilegio).
- Centralizar procesos para reducir dependencia de **Excel y procesos manuales**.
- Implementar **logs y auditoría completa** de acciones.
- Aplicar **cifrado de datos sensibles**.
- Usar **controles de acceso por rol** en todos los sistemas.
- Implementar **monitoreo y alertas** ante actividades sospechosas.
- Aplicar **rate limiting y protección contra caídas del sistema**.

---

## 7. Buenas prácticas de seguridad

Se recomienda adoptar:

- Modelo **Zero Trust**
- **Segmentación de sistemas**
- Actualización constante de software
- Evaluaciones periódicas de vulnerabilidades
- Uso de estándares como ISO 27001

---

## 8. Conclusión

El análisis con STRIDE permitió identificar riesgos importantes en el sistema, especialmente relacionados con procesos manuales, falta de trazabilidad y control de accesos.

Las principales oportunidades de mejora están en:

- Automatización de procesos
- Mejor control de accesos
- Mayor trazabilidad
- Integración de sistemas

Implementar estas mejoras permitirá reducir riesgos y fortalecer la seguridad del sistema, haciéndolo más confiable y robusto. 

Además, se evidencia la necesidad de fortalecer la integración entre sistemas y reducir la dependencia de procesos manuales, los cuales representan uno de los principales riesgos tanto operativos como de seguridad.


---
