# Mapa de infraestructura del sistema real del cliente (BRY Andina)

> **Nota:** Este mapa está construido con base en la transcripción del cliente. Representa la **infraestructura lógica real del proceso operativo**: sistemas, actores, flujos de información e integraciones principales.  
> No incluye detalles de red física, marcas de servidores, IPs, puertos o nube específica porque esa información no aparece explícitamente en la entrevista.

---

## 1. Vista general

```mermaid
flowchart TD
    A[Clientes / Mercado] --> B[Equipo Comercial]
    B --> C[Dynamics 365 / Cotización]
    C --> D[Orden de Compra del Cliente]
    D --> E[Sales Order - SO]
    E --> F[ERP LN]

    F --> G[Operaciones]
    G --> H[Bodegas Regionales<br/>Bogotá / Cali / Barranquilla]
    G --> I[Compras / Purchase Orders - PO]
    I --> J[Proveedores / Subsidiarias Bray]
    J --> K[Importación / Aduana / Nacionalización]
    K --> H

    H --> L[Inventario]
    L --> M[Despacho / Shipping]
    M --> N[Cliente Final]

    F --> O[Order Track]
    O --> G

    F --> P[Financiera]
    P --> Q[Facturación / Cobro]

    F --> R[Power BI / Reportes]
    F --> S[Excel / Seguimiento manual]
```
