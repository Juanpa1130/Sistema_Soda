# Diagrama de clases

```mermaid
classDiagram
    class Usuario {
        <<abstract>>
        +int idUsuario
        +string nombre
        +string cedula
        +string correo
        +string passwordHash
        +bool activo
        +registrarse()
        +iniciarSesion()
        +cerrarSesion()
        +consultarPerfil()
        +editarPerfil()
    }

    class Cliente {
        +int idCliente
        +consultarHistorialPedidos()
        +consultarHistorialPagos()
    }

    class Empleado {
        +int idEmpleado
        +string puesto
        +actualizarEstadoPedido()
    }

    class Administrador {
        +int idAdministrador
        +gestionarUsuarios()
        +gestionarCatalogo()
    }

    class Pedido {
        +int idPedido
        +datetime fecha
        +string estado
        +float totalEstimado
        +agregarPlatillo()
        +agregarBebida()
        +calcularTotal()
        +cambiarEstado()
    }

    class Platillo {
        +int idPlatillo
        +string nombre
        +string descripcion
        +float precio
        +bool disponible
        +actualizarPrecio()
        +cambiarDisponibilidad()
    }

    class Bebida {
        +int idBebida
        +string nombre
        +string descripcion
        +float precio
        +bool disponible
        +actualizarPrecio()
        +cambiarDisponibilidad()
    }

    class MetodoPago {
        +int idMetodoPago
        +string nombre
        +string descripcion
        +bool activo
        +crearMetodoPago()
        +buscarMetodoPago()
        +editarMetodoPago()
        +eliminarMetodoPago()
    }

    class Pago {
        +int idPago
        +float subtotal
        +float total
        +datetime fechaPago
        +string estadoPago
        +calcularTotal()
        +procesarPago()
    }

    class RepositorioDatos {
        +guardar()
        +buscarPorId()
        +actualizar()
        +eliminar()
    }

    Usuario <|-- Cliente
    Usuario <|-- Empleado
    Usuario <|-- Administrador

    Cliente "1" --> "0..*" Pedido : realiza
    Empleado "0..1" --> "0..*" Pedido : atiende
    Pedido "1" --> "0..*" Platillo : incluye
    Pedido "1" --> "0..*" Bebida : incluye
    Pedido "1" --> "0..1" Pago : genera
    MetodoPago "1" --> "0..*" Pago : aplica en

    RepositorioDatos <.. Usuario : persiste
    RepositorioDatos <.. Pedido : persiste
    RepositorioDatos <.. Platillo : persiste
    RepositorioDatos <.. Bebida : persiste
    RepositorioDatos <.. Pago : persiste
