# Arquitectura inicial del sistema

## Diagrama de arquitectura

```mermaid
flowchart TD

subgraph ACTORES["ACTORES"]
    Cliente["Cliente"]
    Seller["Seller"]
    Admin["Administrador"]
end

subgraph PRESENTACION["PRESENTACIÓN"]
    Web["Aplicación Web - API REST"]
end

subgraph NEGOCIO["LOGICA DE NEGOCIO"]
    Usuarios["Usuarios"]
    Sellers["Sellers"]
    Catalogo["Catalogo"]
    Carrito["Carrito"]
    Pedidos["Pedidos"]
end

subgraph DATOS["DATOS"]
    BD["Base de datos"]
end

subgraph EXTERNOS["SISTEMAS EXTERNOS"]
    Pago["Pasarela de pago"]
    ERP["ERP"]
    Envio["Servicio de envio"]
end

ACTORES --> PRESENTACION
PRESENTACION --> NEGOCIO
NEGOCIO --> DATOS
DATOS -->|integraciones| EXTERNOS

Cliente ~~~ Seller
Seller ~~~ Admin
Usuarios ~~~ Sellers
Sellers ~~~ Catalogo
Catalogo ~~~ Carrito
Carrito ~~~ Pedidos
Pago ~~~ ERP
ERP ~~~ Envio

style ACTORES fill:#222,stroke:#fff,stroke-width:2px,color:#fff
style PRESENTACION fill:#222,stroke:#fff,stroke-width:2px,color:#fff
style NEGOCIO fill:#222,stroke:#fff,stroke-width:2px,color:#fff
style DATOS fill:#222,stroke:#fff,stroke-width:2px,color:#fff
style EXTERNOS fill:#222,stroke:#fff,stroke-width:2px,color:#fff
```

## Descripción

La arquitectura inicial se organiza en tres capas principales:

- **Presentación:** permite la interacción de los usuarios con el sistema mediante la aplicación web y la API REST.
- **Lógica de negocio:** contiene los principales módulos responsables de las funcionalidades del sistema: usuarios, sellers, catálogo, carrito y pedidos.
- **Datos:** permite almacenar y consultar la información mediante una base de datos.

Además, el módulo de **Pedidos** se integra con sistemas externos como la **pasarela de pago** y el **servicio de envío**.
