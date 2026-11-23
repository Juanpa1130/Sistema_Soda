# Diagrama de clases
```mermaid
classDiagram
    Usuario <|-- Cliente
    Usuario <|-- Empleado
    Usuario <|-- Administrador
    Usuario : +int ID
    Usuario : +string nombre
    Usuario : +string cedula
    Usuario : +string correo
    Usuario : +string contraseña
    class Cliente{
        +int IDCliente
        +crearCliente()
        +buscarCliente()
        +editarCliente()
        +eliminarCliente()
        +historialPedidos()
        +historialPagos()
    }
    class Empleado{
        +int IDEmpleado
        +string puesto
        +crearEmpleado()
        +buscarEmpleado()
        +editarEmpleado()
        +eliminarEmpleado()
    }
    class Administrador{
        +int IDAdministrador
        +crearAdministrador()
        +buscarAdministrador()
        +editarAdministrador()
        +eliminarAdministrador()     
    }
    class Pedido{
        +int IDPedido
        +int IDCliente
        +int IDEmpleado
        +int IDPlatillo
        +int IDBebida
        +datetime fecha
        +estado bool
        +crearPedido()
        +buscarPedido()
        +editarPedido()
        +eliminarPedido() 
    }
    class Platillo{
        +int IDPlatillo
        +string nombre
        +float precio
        +crearPlatillo()
        +buscarPlatillo()
        +editarPlatillo()
        +eliminarPlatillo() 
    }
    class Bebida{
        +int IDBebida
        +string nombre
        +float precio
        +crearBebida()
        +buscarBebida()
        +editarBebida()
        +eliminarBebida() 
    }
    class MetodoPago{
        +int IDMetodoPago
        +int IDPedido
        +crearmetodoPago()
        +buscarmetodoPago()
        +editarmetodoPago()
        +eliminarmetodoPago() 
    }
    class Pago{
        +int IDPago
        +int IDMetodoPago
        +int IDPedido
        +float subtotal
        +int total
        +crearPago()
        +buscarPago()
        +editarPago()
        +eliminarPago() 
    }

    Cliente "1" --> "0..*" Pedido
    Empleado "1" --> "0..*" Pedido
    Bebida "1" --> "0..*" Pedido
    Platillo "1" --> "0..*" Pedido
    Pedido "1" --> "1" Pago
    MetodoPago "1" --> "1" Pago
