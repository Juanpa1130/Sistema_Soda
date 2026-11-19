# C4 - Nivel 3 - Componentes

## Objetivo

Mostrar los componentes internos del Backend.

```mermaid
flowchart TD

API["Backend"]

Usuarios["Gestión de Usuarios"]
Menu["Gestión de Menú"]
Pedidos["Gestión de Pedidos"]
Pagos["Gestión de Pagos"]
Notificaciones["Notificaciones"]
Reportes["Reportes"]

API --> Usuarios
API --> Menu
API --> Pedidos
API --> Pagos
API --> Notificaciones
API --> Reportes
```

## Componentes

### Gestión de Usuarios

- Login
- Roles
- Permisos

### Gestión de Menú

- Productos
- Categorías
- Activación y desactivación

### Gestión de Pedidos

- Carrito
- Estados
- Historial

### Gestión de Pagos

- Efectivo
- Tarjeta
- SINPE

### Notificaciones

- Pedido listo
- Cambios de estado

### Reportes

- Ventas
- Productos vendidos
- Indicadores de negocio