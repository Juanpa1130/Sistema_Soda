# Diagramas de Secuencia - Sistema Soda

Los participantes corresponden a los componentes de la arquitectura: Aplicación web, Panel de cocina, API Backend y Base de datos. Cada diagrama indica los requerimientos funcionales (RF) que cubre, según `docs/01-requisitos/requisitos.md`.

| # | Diagrama | Actor | Requerimientos |
|---|---|---|---|
| 1 | Iniciar sesión | Usuario (cualquier rol) | RF-20 |
| 2 | Realizar pedido | Cliente | RF-02 a RF-08, RF-18 |
| 3 | Consultar estado del pedido | Cliente | RF-09, RF-11 |
| 4 | Preparar pedido y notificar | Personal de cocina | RF-10 a RF-14, RF-17, RF-25 |
| 5 | Registrar pago | Mesero/Cajero | RF-15, RF-16 |
| 6 | Generar reportes | Administrador | RF-23, RF-24 |

## 1. Iniciar sesión (RF-20)

```mermaid
sequenceDiagram
    autonumber
    actor US as Usuario
    participant WEB as Aplicación web
    participant API as API Backend
    participant DB as Base de datos

    US->>WEB: Ingresa sus credenciales
    WEB->>API: Envía credenciales
    API->>DB: Consulta usuario y rol
    DB-->>API: Datos del usuario

    alt Credenciales válidas
        API-->>WEB: Sesión iniciada y rol
        WEB-->>US: Muestra la pantalla según su rol
    else Credenciales inválidas
        API-->>WEB: Acceso denegado
        WEB-->>US: Muestra mensaje de error
    end
```

## 2. Realizar pedido (RF-02 a RF-08, RF-18)

```mermaid
sequenceDiagram
    autonumber
    actor CL as Cliente
    participant WEB as Aplicación web
    participant API as API Backend
    participant DB as Base de datos
    participant CO as Panel de cocina

    CL->>WEB: Abre el menú
    WEB->>API: Solicita el menú activo
    API->>DB: Consulta productos activos
    DB-->>API: Productos
    API-->>WEB: Menú
    WEB-->>CL: Muestra el menú

    CL->>WEB: Elige un plato personalizable
    WEB->>API: Solicita opciones del plato
    API->>DB: Consulta proteínas y guarniciones
    DB-->>API: Opciones del plato
    API-->>WEB: Opciones disponibles
    WEB-->>CL: Muestra proteínas y guarniciones

    CL->>WEB: Elige opciones y observaciones

    alt Proteína seleccionada
        WEB->>API: Agrega producto al pedido
        API-->>WEB: Detalle con precio recalculado
        WEB-->>CL: Muestra detalle y total
    else Sin proteína
        WEB-->>CL: Solicita elegir una proteína
    end

    CL->>WEB: Confirma el pedido
    WEB->>API: Confirma el pedido
    API->>DB: Guarda pedido (estado Recibido)
    DB-->>API: Número de orden único
    API->>CO: Envía la nueva comanda
    API-->>WEB: Pedido confirmado y número
    WEB-->>CL: Muestra el número de orden
```

## 3. Consultar estado del pedido (RF-09, RF-11)

```mermaid
sequenceDiagram
    autonumber
    actor CL as Cliente
    participant WEB as Aplicación web
    participant API as API Backend
    participant DB as Base de datos

    CL->>WEB: Consulta el estado de su pedido
    WEB->>API: Solicita el estado
    API->>DB: Consulta el estado del pedido
    DB-->>API: Estado actual
    API-->>WEB: Estado del pedido
    WEB-->>CL: Muestra el estado actual
```

Estados posibles: Recibido, En preparación, Listo, Entregado y Cancelado (RF-10).

## 4. Preparar pedido y notificar (RF-10 a RF-14, RF-17, RF-25)

```mermaid
sequenceDiagram
    autonumber
    actor PC as Personal de cocina
    participant CO as Panel de cocina
    participant API as API Backend
    participant DB as Base de datos
    participant WEB as Aplicación web
    actor CL as Cliente

    PC->>CO: Abre las comandas
    CO->>API: Solicita pedidos pendientes
    API->>DB: Consulta pedidos pendientes
    DB-->>API: Pedidos con observaciones
    API-->>CO: Comandas ordenadas por ingreso
    CO-->>PC: Muestra comandas y observaciones

    PC->>CO: Cambia el estado a En preparación
    CO->>API: Actualiza el estado
    API->>DB: Guarda el nuevo estado
    DB-->>API: Estado guardado
    API->>WEB: Refleja el cambio de estado

    PC->>CO: Marca el pedido como Listo
    CO->>API: Actualiza el estado a Listo
    API->>DB: Guarda el nuevo estado
    DB-->>API: Estado guardado
    API->>WEB: Envía notificación de pedido listo
    WEB-->>CL: Avisa y muestra el número de orden
    API-->>CO: Confirmación
    CO-->>PC: Muestra el pedido como Listo
```

## 5. Registrar pago (RF-15, RF-16)

```mermaid
sequenceDiagram
    autonumber
    actor CA as Mesero/Cajero
    participant WEB as Aplicación web
    participant API as API Backend
    participant DB as Base de datos

    CA->>WEB: Selecciona el pedido a cobrar
    WEB->>API: Solicita el pedido
    API->>DB: Consulta pedido y total
    DB-->>API: Pedido y total
    API-->>WEB: Datos del pedido
    WEB-->>CA: Muestra el total

    CA->>WEB: Elige efectivo, tarjeta o SINPE Móvil
    WEB->>API: Registra el pago
    API->>DB: Guarda el pago del pedido

    alt Pago registrado
        DB-->>API: Pago guardado
        API-->>WEB: Pago registrado
        WEB-->>CA: Muestra el comprobante
    else Error al registrar
        DB-->>API: Error
        API-->>WEB: Pago no registrado
        WEB-->>CA: Muestra mensaje de error
    end
```

## 6. Generar reportes (RF-23, RF-24)

```mermaid
sequenceDiagram
    autonumber
    actor AD as Administrador
    participant WEB as Aplicación web
    participant API as API Backend
    participant DB as Base de datos

    AD->>WEB: Elige tipo de reporte y periodo
    WEB->>API: Solicita el reporte
    API->>DB: Consulta ventas, pedidos y productos
    DB-->>API: Datos del periodo
    API-->>WEB: Reporte generado
    WEB-->>AD: Muestra el reporte
```

