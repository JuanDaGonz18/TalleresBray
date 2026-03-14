# Mapa de infraestructura del sistema real del cliente (Bray Controls Andina)

> **Nota:** Este mapa está construido con base en la información obtenida durante la entrevista con el cliente. Representa la **infraestructura lógica del proceso operativo**, incluyendo actores, sistemas empresariales, flujos de información e integraciones principales.  
> No incluye detalles de infraestructura física como redes, servidores, direcciones IP, puertos o proveedores de nube, ya que dicha información no fue proporcionada durante el levantamiento de información.

# 1. Vista general de la arquitectura

El siguiente diagrama representa el flujo principal de información y los sistemas involucrados en la operación comercial y logística de **Bray Controls Andina**.

```mermaid
flowchart TD

    A[Clientes / Mercado Industrial] --> B[Equipo Comercial]
    
    B --> C[Dynamics 365<br/>Gestión de Cotizaciones]
    
    C --> D[Orden de Compra del Cliente]
    
    D --> E[Ingreso manual de pedido]
    
    E --> F[ERP LN<br/>Sistema central de gestión]

    F --> G[Área de Operaciones]

    G --> H[Bodegas regionales<br/>Bogotá / Cali / Barranquilla]

    G --> I[Gestión de Compras]
    
    I --> J[Purchase Orders - PO]

    J --> K[Proveedores y Subsidiarias Bray]

    K --> L[Importación / Aduanas / Nacionalización]

    L --> H

    H --> M[Inventario]

    M --> N[Despacho / Shipping]

    N --> O[Cliente final]

    F --> P[Order Track<br/>Seguimiento operativo de órdenes]

    P --> G

    F --> Q[Área Financiera]

    Q --> R[Facturación y Cobro]

    F --> S[Power BI<br/>Reportes y analítica]

    F --> T[Excel<br/>Seguimiento manual y control operativo]
