# Ficha de Caracterización del Cliente

**Nombre del Equipo:** ARQTEAM-05

**Integrantes del Equipo:**
- Julián Barragán Pérez
- Juan David González Rubio
- Josue David Sarmiento

**Fecha:** 22 de Enero de 2026

---

## Nombre del Cliente
Bray Controls Andina Ltda

## Organización
Subsidiaria comercial de Bray International en Colombia. Opera bajo el territorio andino y gestiona ventas en países como Ecuador, Venezuela, Perú, Chile, Argentina, Brasil, México y Centroamérica, en coordinación con otras subsidiarias regionales.

---

## I. Información General del Negocio

**Nombre de la empresa o entidad:**
Bray Controls Andina Ltda

**Sector económico:**
Comercialización industrial B2B — Equipos de control de flujo (válvulas, actuadores y sistemas de automatización industrial).

**Número de empleados / usuarios / clientes:**
- Empleados: 45
- Clientes: Empresas industriales del sector petróleo y gas, energía, manufactura, tratamiento de agua, entre otros.

**Ubicación principal:**
Autopista Medellín Km 7.8, Parque Industrial Innova, Bodega 110-111-112 y 113, Tenjo, Cundinamarca.

**Bodegas activas:**
- Bogotá (Tenjo, Cundinamarca) — sede principal
- Cali
- Barranquilla

**Tecnologías principales actuales:**

| Sistema | Rol |
|---------|-----|
| ERP LN | Sistema central corporativo: gestión de pedidos (Sales Orders), inventario, órdenes de compra (PO), despachos y facturación base. Administrado desde Houston. |
| Microsoft Dynamics 365 | CRM: gestión de cotizaciones y relación con clientes. Vinculado al flujo del ERP LN. |
| Microsoft Azure | Infraestructura en nube; backups automáticos cada 4-6 horas. |
| Microsoft Outlook | Comunicación corporativa. |
| Sistema de facturación electrónica | Independiente del ERP; requerido por normativa colombiana. |
| Excel | Seguimiento de planeación, órdenes y procesos complementarios (uso paralelo al ERP). |
| Order Track | Aplicativo adicional para seguimiento de estados de órdenes (en proceso de implementación). |

---

## II. Objetivos Estratégicos

1. Garantizar disponibilidad eficiente de inventario en las tres bodegas para responder rápidamente a clientes industriales.
2. Optimizar el proceso comercial desde cotización hasta facturación, reduciendo tiempos y reprocesos.
3. Mantener integración operativa con subsidiarias corporativas (Bray China, Bray Houston) para compras y abastecimiento internacional.
4. Mejorar la trazabilidad de órdenes a lo largo del proceso operativo (de Sales Order a despacho).
5. Reducir el Slow Moving Inventory (SMI) y prevenir stockouts en ítems de alta rotación.

---

## III. Problemas o Necesidades Identificadas

**Problema #1: Dependencia del inventario y tiempos de importación**

Cuando no hay stock disponible, los tiempos de abastecimiento son largos: 8-10 semanas desde Houston, 20-22 semanas desde China, hasta 7 meses para productos de fabricación especial. Esto dificulta cumplir compromisos de entrega con clientes.

**Problema #2: Gestión manual de órdenes y planeación**

Los procesos de seguimiento de órdenes, planeación de entrega y asignación de inventario dependen en gran medida de Excel y coordinación informal entre áreas (llamadas, correos), lo que genera riesgo de errores, retrasos y falta de visibilidad.

**Problema #3: Separación entre ERP LN y sistema de facturación electrónica**

La factura se genera en LN pero debe procesarse en un sistema separado de facturación electrónica, lo que introduce un paso adicional con riesgo de reprocesos.

**Problema #4: Inventario SMI y stockouts simultáneos**

Coexisten productos con exceso de inventario (SMI) y productos con alta demanda en stockout. La gestión de puntos de reorden (Reorder Points) es manual y no automatizada, lo que dificulta el equilibrio del inventario.

**Problema #5: Baja trazabilidad interna de órdenes**

No existe visibilidad centralizada del estado de una orden a lo largo de su ciclo de vida (cotización → pedido → compra → bodega → ensamble → despacho). El Order Track está siendo implementado para resolver esto, pero aún no está completamente operativo.

**Problema #6: Comunicación interdepartamental no estructurada**

La coordinación entre ventas, operaciones y finanzas depende de canales informales. No existe un sistema o proceso documentado que indique claramente cómo fluye la información entre áreas y qué hacer ante situaciones específicas.

---

## IV. Procesos Clave del Negocio

### 1. Proceso de Cotización

Cliente solicita cotización → Ventas externas canaliza a ventas internas → Ventas internas genera cotización en Dynamics 365 (precio, disponibilidad, opciones) → Cliente evalúa y decide.

### 2. Proceso de Pedido y Abastecimiento

Cliente envía orden de compra → Ventas internas registra pedido en ERP LN y genera trailer → Operaciones verifica inventario en bodegas (Bogotá / Cali / Barranquilla) →

- **Si hay stock:** alistamiento (picking en posición física) → paso a shipping → despacho.
- **Si no hay stock o es producto especial:** se genera Orden de Compra (PO) al corporativo o fábrica → seguimiento internacional → recepción en bodega → ingreso a inventario → despacho.

### 3. Proceso de Despacho y Facturación

Alistamiento de mercancía → Salida de bodega → Generación de Remisión → Remisión dispara proceso de facturación → Departamento financiero procesa factura en sistema de facturación electrónica → Cliente recibe mercancía y factura.

### 4. Proceso de Control de Inventario

Gestión de inventario con FIFO (First In, First Out) → Cycle counting: 3 inventarios por año (meta: contar 25% del inventario por mes) → Ajustes aprobados por coordinadora de operaciones → Reposición de inventario mediante Reorder Points (proceso actualmente manual).

---

## V. Expectativas Frente a la Solución

El cliente espera que la arquitectura propuesta:

- Modele correctamente los flujos reales del negocio, incluyendo las tres bodegas activas.
- Permita trazabilidad completa desde cotización hasta factura.
- Mejore el control de inventario por bodega y facilite la gestión del SMI y stockouts.
- Soporte la distinción entre órdenes de tipo warehouse y direct delivery.
- Sea coherente con el funcionamiento actual del ERP LN y Dynamics 365.
- Permita escalar en caso de apertura de nuevas bodegas o expansión regional.

**Restricciones relevantes:**

- Dependencia del ERP LN corporativo (administrado desde Houston); cambios requieren aprobación del grupo IT de Estados Unidos.
- Normativa colombiana de facturación electrónica.
- Operación B2B industrial con altos estándares técnicos y tiempos de importación internacionales no controlables localmente.
- Soporte IT local limitado (un encargado técnico local: Julián David Rodríguez).

---

## VI. Persona de Contacto

**Nombre del contacto:**
Carlos Hernando Porras López

**Teléfono:**
316 4116484

**Rol o vínculo con la solución:**
Gerente General — Bray Controls Andina Ltda
