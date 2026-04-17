# 📄 Informe Técnico del Taller  

## 🔖 Nombre del Taller  
**Taller 6 - Checklist de Cumplimiento Normativo**

---

## 👥 Integrantes del equipo  
- Julián Barragán  
- Josue Sarmiento 
- Juan Gonzalez

---

## 🧠 Descripción general del trabajo  
El objetivo del taller fue evaluar el nivel de cumplimiento normativo de un sistema real, identificando brechas en aspectos legales, de seguridad de la información y operación, con base en marcos como la Ley 1581 de 2012, Habeas Data y el estándar ISO/IEC 27001.

La actividad se desarrolló a partir de un levantamiento de información en una empresa real (Breandina), donde se analizaron los procesos de ventas, operaciones, inventario y gestión de pedidos. A partir de esta información, se construyó un checklist de cumplimiento que permitió identificar riesgos, debilidades y oportunidades de mejora en el sistema actual.

---

## 🔧 Proceso de desarrollo  
El equipo inició con la recolección de información mediante entrevistas y observación directa de los procesos operativos, especialmente en el flujo de órdenes de venta (Sales Order), compras (Purchase Order), gestión de inventario y despacho.

Posteriormente, se estructuró la información en dos componentes principales:  
1. **Checklist de cumplimiento**, evaluando criterios como protección de datos, seguridad, operación y cumplimiento normativo.  
2. **Matriz de brechas y riesgos**, donde se identificaron los principales problemas del sistema, como el uso de Excel para procesos críticos, la falta de trazabilidad y la ausencia de automatización.

Se utilizaron herramientas como Excel para estructurar la información, análisis cualitativo para evaluar los procesos, y criterios basados en estándares internacionales para clasificar el nivel de cumplimiento.

---

## 🧩 Análisis del modelo propuesto  

### 🔹 Estructura del modelo  
El modelo se basa en un enfoque de evaluación por categorías:

- Datos personales  
- Seguridad de la información  
- Gestión de la información  
- Operación  
- Cumplimiento normativo  

Cada categoría contiene criterios específicos evaluados con niveles de cumplimiento (✅, ⚠️, ❌), junto con evidencia y recomendaciones.

---

### 🔹 Representación de las necesidades del cliente  
El modelo refleja directamente las necesidades de la empresa, ya que se enfoca en:

- Mejorar la trazabilidad de órdenes  
- Reducir la dependencia de procesos manuales  
- Aumentar la seguridad de la información  
- Garantizar cumplimiento legal  

Se identificaron problemas clave como:
- Falta de integración entre sistemas (ERP, Excel, herramientas externas)  
- Procesos manuales en planeación y despacho  
- Problemas de inventario (SMI y stockouts)  
- Falta de visibilidad en tiempo real  

---

### 🔹 Supuestos tomados  
- Se asumió que el ERP (LN) es el sistema principal, pero no cubre completamente las necesidades operativas  
- Se consideró que el uso de Excel representa un riesgo de seguridad y control  
- Se asumió que no existen procesos formales documentados en seguridad y cumplimiento, debido a la dependencia en conocimiento humano  
- Se tomó como base que la empresa maneja datos personales de clientes, lo que implica cumplimiento obligatorio de normativas  

---

## 📋 Tabla de actores, entidades o componentes  

| Nombre del elemento | Tipo | Descripción | Responsable |
|--------------------|------|------------|------------|
| Cliente | Actor | Realiza órdenes de compra | Externo |
| Ventas externas | Actor | Contacto directo con cliente | Comercial |
| Ventas internas | Actor | Genera cotizaciones y gestiona precios | Comercial |
| ERP LN | Sistema | Gestiona órdenes, inventario y compras | TI |
| Excel | Herramienta | Apoyo en planeación y análisis | Operaciones |
| Operaciones | Área | Gestiona pedidos, inventario y despacho | Interno |
| Bodega | Componente | Almacenamiento físico de productos | Operaciones |
| Order Track | Sistema | Seguimiento de órdenes (parcial) | TI |
| Planeador | Actor | Define fechas de entrega | Operaciones |

---

## 🔍 Investigación complementaria  

### Tema investigado:  
**ISO/IEC 27001 y gestión de seguridad de la información**

### Resumen:  
ISO/IEC 27001 es un estándar internacional que define los requisitos para establecer, implementar y mantener un Sistema de Gestión de Seguridad de la Información (SGSI). Su enfoque principal es proteger la confidencialidad, integridad y disponibilidad de la información mediante controles organizacionales, técnicos y físicos.

Este estándar propone una gestión basada en riesgos, donde las organizaciones deben identificar vulnerabilidades, evaluar impactos y definir controles adecuados. Además, incluye prácticas como control de accesos, gestión de incidentes, auditoría y mejora continua.

En el contexto del taller, se evidenció que la empresa no cuenta con un SGSI formal, lo que genera riesgos importantes como falta de trazabilidad, exposición de datos y dependencia de procesos manuales. La implementación de ISO 27001 permitiría estructurar mejor la seguridad, reducir riesgos y mejorar el cumplimiento normativo.

---

## 📚 Referencias  

1. Ley 1581 de 2012 – Protección de Datos Personales (Colombia)  
2. ISO/IEC 27001 – Information Security Management  
3. Habeas Data – Marco constitucional colombiano  
4. OMG. Business Process Model and Notation (BPMN)  
   https://www.omg.org/spec/BPMN/  
