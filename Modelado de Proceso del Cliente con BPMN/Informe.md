# Informe Técnico del Taller

## Nombre del Taller
**Taller 1 – Parte 2: Modelado de Proceso del Cliente con BPMN**

**Equipo:** ARQTEAM-05  
**Integrantes:** Julián Barragán Pérez · Juan David González Rubio · Josue David Sarmiento  
**Cliente:** Bray Controls Andina Ltda  
**Fecha:** 2026

---

## Descripción general del trabajo

El objetivo de este taller fue modelar un proceso de negocio de Bray Controls Andina utilizando la notación BPMN (Business Process Model and Notation), identificando eventos, actividades, decisiones, actores involucrados y puntos críticos dentro del flujo del proceso.

El proceso elegido fue **Gestión de Cotización y Pedido de Cliente Industrial**, ya que constituye la actividad central dentro del modelo de negocio B2B de la empresa. Este proceso integra áreas comerciales, operativas y financieras, y se apoya en el sistema ERP LN como herramienta principal de gestión.

La selección de este proceso se fundamentó en que:

- Representa el flujo de mayor impacto en la operación y en la relación con el cliente.
- Involucra múltiples áreas internas (ventas externas, ventas internas, operaciones y finanzas).
- Evidencia las principales dependencias tecnológicas y puntos de decisión críticos de la empresa.

---

## Proceso de desarrollo

Para el desarrollo del modelo BPMN se siguieron las siguientes etapas:

### 1. Comprensión del negocio del cliente

Se analizó la información levantada en visitas y entrevistas con personal clave de Bray Controls Andina, incluyendo el área operativa (Angélica), el área comercial (Felipe / ventas internas) y el encargado técnico (Julián David Rodríguez). Esta información permitió entender el modelo operativo real de la empresa, su estructura organizacional y su relación con el corporativo internacional (Bray International, Houston).

### 2. Selección del proceso

Se eligió el proceso de cotización y gestión de pedidos porque:

- Involucra múltiples áreas de la organización.
- Es el proceso que directamente genera valor y determina la experiencia del cliente.
- Presenta puntos de decisión críticos relacionados con inventario, abastecimiento y tiempos de entrega.

### 3. Identificación de actores

Se identificaron los participantes clave dentro del proceso:

- Cliente industrial
- Ventas externas (ingenieros de campo)
- Ventas internas (gestión de cotizaciones y precios)
- Área de operaciones / logística
- Área financiera
- Sistema ERP LN (corporativo)
- Sistema Dynamics 365 (cotizaciones)

### 4. Construcción del flujo inicial

Se definieron los eventos de inicio y fin, las actividades principales y los puntos de decisión, como la verificación de disponibilidad de inventario en las bodegas (Bogotá, Cali y Barranquilla) y la necesidad de generar órdenes de compra al corporativo.

### 5. Refinamiento del modelo

Se incorporaron compuertas BPMN, flujos alternos y validaciones hasta obtener un modelo coherente con el funcionamiento real del proceso confirmado en las entrevistas.

La herramienta utilizada para el modelado fue **Draw.io (diagrams.net)** por su soporte nativo para diagramas BPMN y facilidad de colaboración.

---

## Análisis del modelo propuesto

El modelo BPMN se estructura mediante varios carriles (swimlanes) que representan las áreas organizacionales involucradas: Cliente, Ventas Externas, Ventas Internas, Operaciones y Finanzas. Esta estructura permite visualizar de manera clara las responsabilidades de cada área y los puntos de transferencia de información entre ellas.

### Flujo principal

El flujo inicia con la **solicitud de cotización** por parte del cliente industrial. El vendedor externo canaliza la solicitud al área de ventas internas, que es quien tiene acceso al ERP LN y al sistema Dynamics 365 para generar la cotización formal.

Una vez el cliente envía su **orden de compra**, ventas internas registra el pedido en el ERP LN y genera un documento (trailer) que se remite al área de operaciones. Operaciones verifica la disponibilidad de inventario en las bodegas activas de la empresa.

**Flujo con inventario disponible:** Si el producto se encuentra disponible en bodega (Bogotá, Cali o Barranquilla), se procede con el alistamiento, picking y despacho de la mercancía.

**Flujo sin inventario disponible:** Si no hay stock o se trata de un producto especial, se genera una orden de compra (Purchase Order) al corporativo o subsidiaria correspondiente (Bray Houston o Bray China). En estos casos el tiempo de abastecimiento puede oscilar entre 8 y 22 semanas dependiendo del origen del material, lo que impacta directamente la fecha de entrega al cliente.

Una vez la mercancía está lista para despacho, operaciones genera la **Remisión**, que es el evento que dispara el proceso de facturación en el área financiera. La factura se procesa en el sistema de facturación electrónica conforme a la normativa colombiana.

### Elementos relevantes del modelo

El modelo refleja los siguientes aspectos del funcionamiento real del negocio:

- La distinción entre ventas externas (cara al cliente) y ventas internas (acceso a sistemas y precios), que operan como equipo integrado.
- La dependencia del inventario local para tiempos de respuesta ágiles, frente a los largos tiempos de abastecimiento desde el corporativo.
- El uso de múltiples herramientas (Dynamics 365 para cotizaciones, ERP LN para pedidos, inventario y compras, Excel para seguimiento y planeación).
- El rol de la Remisión como evento disparador de la facturación.
- El cumplimiento de facturación electrónica según normativa colombiana.

### Supuestos del modelo

- El ERP LN gestiona la información de inventario, pedidos y órdenes de compra al corporativo.
- Las órdenes de compra al corporativo se generan cuando el inventario local es insuficiente o se trata de producto especial.
- El cliente confirma el pedido después de recibir y aceptar la cotización formal.
- Las bodegas activas son Bogotá (sede principal), Cali y Barranquilla.

---

## Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Cliente Industrial | Actor | Empresa que solicita cotizaciones y realiza compras | Cliente |
| Ventas Externas | Actor | Ingenieros de campo que visitan clientes y canalizan solicitudes | Bray Controls Andina |
| Ventas Internas | Actor | Área que gestiona cotizaciones, registra pedidos y maneja precios y costos | Bray Controls Andina |
| Operaciones / Logística | Actor | Área responsable del control de inventario, compras y despacho | Bray Controls Andina |
| Finanzas | Actor | Área encargada de la facturación y gestión de cobros | Bray Controls Andina |
| ERP LN | Sistema | Sistema corporativo de gestión empresarial: pedidos, inventario y compras | Corporativo (Houston) |
| Dynamics 365 | Sistema | Herramienta CRM para gestión de cotizaciones y clientes | Corporativo (Houston) |
| Inventario | Entidad | Productos disponibles en bodegas de Bogotá, Cali y Barranquilla | Operaciones |
| Orden de Compra (PO) | Documento | Solicitud de compra realizada al corporativo o subsidiaria | Operaciones |
| Remisión | Documento | Confirmación de salida de mercancía que activa el proceso de facturación | Operaciones |
| Factura Electrónica | Documento | Documento fiscal generado conforme a normativa colombiana | Finanzas |

---

## Investigación complementaria

### Buenas prácticas en modelado BPMN

Las buenas prácticas en BPMN recomiendan mantener los modelos claros y comprensibles, con eventos de inicio y fin bien definidos, evitando cruces innecesarios de flujos y utilizando compuertas para representar decisiones dentro del proceso.

Se recomienda utilizar swimlanes para separar responsabilidades organizacionales, lo cual facilita la comprensión del proceso tanto para perfiles técnicos como para usuarios del negocio. En el caso de Bray Controls Andina, esta práctica fue especialmente útil para evidenciar la separación de roles entre ventas externas, ventas internas y operaciones, que aunque trabajan de forma integrada, tienen responsabilidades y accesos diferenciados.

Otra recomendación importante es modelar únicamente el nivel de detalle necesario para el objetivo del análisis. BPMN permite representar tanto actividades manuales como procesos automatizados, lo cual resultó relevante en este caso dado el uso mixto de herramientas (ERP LN, Dynamics 365, Excel y seguimiento manual) que caracteriza la operación actual.

Estas buenas prácticas fueron aplicadas en el desarrollo del modelo, permitiendo estructurar el proceso de forma clara e identificando decisiones clave como la disponibilidad de inventario, la generación de órdenes de compra al corporativo y el rol de la remisión como evento disparador de la facturación.

---

## Referencias

Object Management Group (OMG). *Business Process Model and Notation (BPMN) Version 2.0*.  
https://www.omg.org/spec/BPMN/

Silver, Bruce. *BPMN Method and Style*. Cody-Cassidy Press, 2011.

Dumas, Marlon; La Rosa, Marcello; Mendling, Jan; Reijers, Hajo. *Fundamentals of Business Process Management*. Springer, 2018.
