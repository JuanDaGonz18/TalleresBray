# Informe Técnico del Taller

## Nombre del Taller  
**Taller 1 – Parte 2: Modelado de Proceso del Cliente con BPMN**

---

## Descripción general del trabajo

El objetivo de este taller fue modelar un proceso de negocio utilizando la notación BPMN (Business Process Model and Notation), identificando eventos, actividades, decisiones, actores involucrados y puntos críticos dentro del flujo del proceso.

Inicialmente se trabajó con el caso base de la Clínica Salud Viva con el fin de comprender la estructura y los elementos del modelado BPMN. Posteriormente, el equipo aplicó los conocimientos adquiridos al cliente real asignado, **Bray Controls Andina**, seleccionando un proceso representativo de su operación comercial.

El proceso elegido fue **Gestión de Cotización y Pedido de Cliente Industrial**, ya que constituye una actividad central dentro del modelo de negocio B2B de la empresa. Este proceso integra áreas comerciales, operativas y financieras, además de la interacción con el sistema ERP corporativo.

---

## Proceso de desarrollo

Para el desarrollo del modelo BPMN se siguieron las siguientes etapas:

### 1. Comprensión del negocio del cliente
Se analizó la información disponible sobre Bray Controls Andina, su modelo operativo, estructura organizacional y relación con el corporativo internacional.

### 2. Selección del proceso
Se eligió el proceso de cotización y gestión de pedidos porque involucra múltiples áreas y representa una parte esencial de la operación comercial de la empresa.

### 3. Identificación de actores
Se identificaron los participantes clave dentro del proceso:

- Cliente industrial  
- Área de ventas internas  
- Área de operaciones / logística  
- Área financiera  
- Sistema ERP corporativo  

### 4. Construcción del flujo inicial
Se definieron los eventos de inicio y fin, las actividades principales y los puntos de decisión, como la verificación de disponibilidad de inventario.

### 5. Refinamiento del modelo
Se incorporaron compuertas BPMN, flujos alternos y validaciones hasta obtener un modelo coherente con el funcionamiento esperado del proceso.

La herramienta utilizada para el modelado fue **Draw.io (diagrams.net)** debido a su facilidad de uso y soporte para diagramas BPMN.

---

## Análisis del modelo propuesto

El modelo BPMN se estructura mediante varios carriles (swimlanes) que representan las áreas organizacionales involucradas: Cliente, Ventas, Operaciones y Finanzas. Esta estructura permite visualizar de manera clara las responsabilidades de cada área y los puntos de transferencia de información entre ellas.

El flujo inicia con la solicitud de cotización por parte del cliente. Posteriormente, el área de ventas verifica la disponibilidad de los productos en el sistema ERP. Si el producto se encuentra disponible en inventario, se genera la cotización y posteriormente se registra el pedido del cliente.

En caso de no contar con inventario disponible, se genera una orden de compra al corporativo o proveedor correspondiente, lo que introduce un flujo alternativo dentro del proceso. Una vez el producto está disponible, se procede con la preparación del despacho y la emisión de la factura electrónica al cliente.

El modelo refleja varios elementos relevantes del funcionamiento del negocio:

- La dependencia del inventario local para responder rápidamente a los pedidos.
- La interacción con el corporativo para el abastecimiento de productos.
- El uso del ERP como sistema central para la gestión de información.
- El cumplimiento de procesos de facturación electrónica conforme a la normativa colombiana.

Los principales supuestos utilizados en el modelo fueron los siguientes:

- El ERP LN gestiona la información de inventario y pedidos.
- Las órdenes de compra al corporativo se generan cuando el inventario local no es suficiente.
- El cliente confirma el pedido después de recibir y aceptar la cotización.

---

## Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Cliente Industrial | Actor | Empresa que solicita cotizaciones y realiza compras | Cliente |
| Ventas Internas | Actor | Área encargada de gestionar cotizaciones y registrar pedidos | Bray Controls Andina |
| Operaciones / Logística | Actor | Área responsable del control de inventario y abastecimiento | Bray Controls Andina |
| Finanzas | Actor | Área encargada de la facturación y gestión de cobros | Bray Controls Andina |
| ERP LN | Sistema | Sistema corporativo de gestión empresarial utilizado para registrar pedidos e inventario | Corporativo |
| Inventario | Entidad | Productos disponibles en la bodega local | Operaciones |
| Orden de Compra | Documento | Solicitud de compra realizada al corporativo o proveedor | Operaciones |

---

## Investigación complementaria

### Tema investigado: Buenas prácticas en modelado BPMN

Las buenas prácticas en BPMN recomiendan mantener los modelos claros y comprensibles, con eventos de inicio y fin bien definidos, evitando cruces innecesarios de flujos y utilizando compuertas para representar decisiones dentro del proceso.

También se recomienda utilizar swimlanes para separar responsabilidades organizacionales, lo cual facilita la comprensión del proceso tanto para perfiles técnicos como para usuarios del negocio.

Otra recomendación importante es modelar únicamente el nivel de detalle necesario para el objetivo del análisis. Un exceso de complejidad puede dificultar la interpretación del proceso y reducir la utilidad del modelo.

BPMN permite representar tanto actividades manuales como procesos automatizados, lo cual resulta especialmente útil en organizaciones que integran sistemas ERP con actividades humanas. En el caso de Bray Controls Andina, el modelo permite visualizar claramente la interacción entre el sistema ERP y las áreas organizacionales involucradas en el proceso de cotización y pedido.

Estas buenas prácticas fueron aplicadas en el desarrollo del modelo del taller, permitiendo estructurar el proceso de forma clara y comprensible, identificando decisiones clave como la disponibilidad de inventario y la interacción con el corporativo.

---

## Referencias

Object Management Group (OMG). *Business Process Model and Notation (BPMN) Version 2.0*.  
https://www.omg.org/spec/BPMN/

Silver, Bruce. *BPMN Method and Style*. Cody-Cassidy Press, 2011.

Dumas, Marlon; La Rosa, Marcello; Mendling, Jan; Reijers, Hajo. *Fundamentals of Business Process Management*. Springer, 2018.