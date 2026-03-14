# Taller 2: Modelo de Información y Diagrama de Contexto

## Integrantes

- Julián Barragán Pérez
- Juan David González Rubio
- Josue David Sarmiento


# 1. Introducción

El presente documento describe el modelo de información (ERD) y el diagrama de contexto desarrollados para Bray Andina, subsidiaria corporativa de Bray International en Colombia.

A diferencia del caso base hospitalario trabajado en clase, este modelo se adapta a un dominio empresarial B2B de comercialización industrial, donde no existe fabricación local sino importación, almacenamiento, ensamble y distribución de válvulas y sistemas de control de fluidos.

El objetivo fue modelar correctamente las entidades de información y los flujos reales del proceso comercial, asegurando coherencia con la operación actual de la compañía.

---

# 2. Análisis del Dominio

Bray Andina es una empresa comercializadora industrial que:

- Compra productos a subsidiarias del mismo corporativo (Bray China, Bray Houston).
- Mantiene inventario local en bodega.
- Gestiona cotizaciones a través del departamento de ventas internas.
- Procesa pedidos de clientes industriales.
- Genera órdenes de compra (PO) al corporativo cuando es necesario.
- Despacha mercancía desde su bodega.
- Genera remisiones que disparan el proceso de facturación.
- Utiliza el ERP LN como sistema principal.
- Usa un sistema adicional para facturación electrónica.

No existe fabricación local; únicamente se realizan actividades de ensamble y comercialización.

---

# 3. Modelo de Información (ER)

## 3.1 Entidades Principales

### Cliente
- id_cliente (PK)
- nombre_empresa
- NIT
- direccion
- sector_industrial
- contacto_principal
- email
- telefono

---

### Producto
- id_producto (PK)
- nombre
- tipo_producto
- especificacion_tecnica
- precio_base
- estado

---

### Cotizacion
- id_cotizacion (PK)
- fecha
- estado
- valor_estimado
- id_cliente (FK)
- id_vendedor_interno (FK)

Generada por el departamento de ventas internas.

---

### Detalle_Cotizacion
- id_detalle_cotizacion (PK)
- id_cotizacion (FK)
- id_producto (FK)
- cantidad
- precio_unitario

---

### Pedido
- id_pedido (PK)
- fecha
- estado
- total
- id_cliente (FK)
- id_cotizacion (FK)

Se genera cuando el cliente envía la orden de compra.

---

### Detalle_Pedido
(Entidad intermedia para resolver relación N:M)

- id_detalle (PK)
- id_pedido (FK)
- id_producto (FK)
- cantidad
- precio_unitario

---

### Orden_Compra (PO)
- id_po (PK)
- fecha
- estado
- id_pedido (FK)
- proveedor_corporativo

Se genera manualmente en el ERP LN cuando:
- El producto es especial.
- No hay stock disponible.
- Se requiere reposición.

---

### Detalle_Orden_Compra
- id_detalle_po (PK)
- id_po (FK)
- id_producto (FK)
- cantidad
- costo_unitario

---

### Bodega
- id_bodega (PK)
- nombre
- ubicacion

Actualmente existe una única bodega local.

---

### Inventario
- id_inventario (PK)
- id_producto (FK)
- id_bodega (FK)
- cantidad_disponible

---

### Remision
- id_remision (PK)
- fecha
- id_pedido (FK)
- estado_despacho

Evento del sistema que confirma la salida de mercancía y dispara el proceso de facturación.

---

### Factura
- id_factura (PK)
- fecha
- valor_total
- estado
- id_pedido (FK)

Generada en LN y posteriormente utilizada en el sistema de facturación electrónica.

---

### Empleado
- id_empleado (PK)
- nombre
- cargo
- area
- email

Roles relevantes:
- Ventas internas
- Ventas externas
- Operaciones
- Financiero

---

# 3.2 Relaciones y Cardinalidades

- Cliente 1 — N Cotizacion  
- Cotizacion 1 — 0..N Pedido
- Pedido 1 — N Detalle_Pedido  
- Producto 1 — N Detalle_Pedido  
- Cotizacion 1 — N Detalle_Cotizacion
- Producto 1 — N Detalle_Cotizacion
- Pedido 1 — N Orden_Compra  
- Orden_Compra 1 — N Detalle_Orden_Compra
- Producto 1 — N Detalle_Orden_Compra
- Producto 1 — N Inventario  
- Bodega 1 — N Inventario  
- Pedido 1 — 1 Remision  
- Pedido 1 — 1 Factura  
- Empleado 1 — N Cotizacion  

---

# 4. Proceso Comercial Modelado

El flujo real identificado es el siguiente:

1. Cliente solicita cotización.
2. Ventas externas canaliza solicitud a ventas internas.
3. Ventas internas genera la cotización en el ERP LN.
4. Cliente envía orden de compra.
5. Se crea Pedido en el sistema.
6. Si no hay inventario o es producto especial, se genera Orden de Compra (PO) al corporativo.
7. Producto llega a bodega.
8. Se genera Remisión cuando la mercancía sale.
9. La remisión dispara la facturación.
10. El departamento financiero ejecuta la factura.
11. Factura se procesa en sistema de facturación electrónica.

---

# 5. Diagrama de Contexto
**Archivo:** `ERD_BRY_Andina.drawio.png`

<img src="ERD_BRY_Andina.drawio.png" alt="Diagrama de contexto" style="max-width:100%;height:auto;" />

## 5.1 Sistema Central

ERP LN – Sistema de Gestión Empresarial Bray Andina

---

## 5.2 Actores Internos

- Ventas Internas
- Ventas Externas
- Operaciones (compras, logística, comercio exterior)
- Departamento Financiero

---

## 5.3 Actores Externos

- Cliente Industrial
- Subsidiarias Corporativas (Bray China / Bray Houston)
- Sistema de Facturación Electrónica

---

## 5.4 Flujos de Información

Cliente → Solicitud de cotización  
Ventas Internas → Cotización en LN  

Cliente → Orden de compra  
Sistema → Pedido  

Sistema → Orden de Compra (PO) → Corporativo  

Corporativo → Confirmación de suministro  

Sistema → Remisión (salida de mercancía)  

Remisión → Dispara facturación  

LN → Factura base → Sistema de Facturación Electrónica  

Factura → Cliente  

---

# 6. Decisiones de Modelado

## 6.1 Eliminación de Producción

Se eliminó la entidad Orden_Produccion del modelo inicial debido a que Bray Andina no fabrica productos; únicamente compra al corporativo y comercializa.

---

## 6.2 Separación de Orden de Compra

Se modeló Orden_Compra como entidad independiente para representar la relación comercial con subsidiarias del corporativo.

---

## 6.3 Inventario por Bodega

Se separó Inventario de Producto para permitir control por ubicación física, aunque actualmente exista una sola bodega.

---

## 6.4 Remisión como Evento Disparador

Se incluyó Remision como entidad formal porque representa el evento que activa el proceso de facturación.

---

## 7. Diferencia Frente al Caso Base

Caso base hospitalario:
- Paciente
- Cita
- Médico
- Factura

Modelo Bray Andina:
- Cliente
- Cotización
- Pedido
- Orden de Compra
- Inventario
- Remisión
- Factura

El modelo refleja un dominio de comercialización industrial B2B, claramente distinto al dominio clínico trabajado en clase.

---

# 8. Conclusión

El modelo desarrollado representa de manera estructurada el proceso comercial real de Bray Andina, alineado con su operación como subsidiaria comercial del corporativo Bray International.

Se aplicaron principios de normalización, separación de responsabilidades y coherencia con el dominio empresarial, logrando un modelo consistente tanto en el ERD como en el diagrama de contexto.

La adaptación demuestra comprensión del negocio real y diferenciación clara respecto al caso base académico.

## Licencia

Material del curso de Arquitectura Empresarial — Universidad de La Sabana. Uso académico bajo licencia MIT.