# C4 - Nivel 1 - Diagrama de Contexto

## Objetivo

Mostrar cómo interactúan los actores principales con el sistema.

```mermaid
flowchart LR

Cliente[Cliente]
Mesero[Mesero/Cajero]
Cocina[Personal de Cocina]
Administrador[Administrador]

Sistema["Sistema de Pedidos para Soda"]

Cliente -->|Realiza pedidos| Sistema
Mesero -->|Gestiona pedidos| Sistema
Cocina -->|Actualiza estados| Sistema
Administrador -->|Administra el sistema| Sistema
```

## Actores

### Cliente
- Realiza pedidos.
- Consulta el estado de órdenes.
- Recibe notificaciones.

### Mesero / Cajero
- Gestiona órdenes.
- Registra pagos.

### Personal de Cocina
- Consulta comandas.
- Actualiza estados.

### Administrador
- Gestiona productos.
- Consulta reportes.
- Administra usuarios.