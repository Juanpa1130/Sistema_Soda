## 1. Requerimientos Funcionales

| Requerimiento Funcional | Descripción |
| Gestión de menú | El sistema deberá permitir registrar, modificar, activar y desactivar productos del menú. | 
| Configuración de platos | El sistema deberá permitir configurar platos personalizables con sus respevtivas opciones | 
| Selección de proteína | El sistema deberá obligar al cliente a seleccionar una proteína antes de agregar un casado al pedido. | 
| Selección de guarniciones | El sistema deberá permitir al cliente elegir guarniciones incluidas y adicionales. | 
| Cálculo automático de precio | El sistema deberá actualizar automáticamente el precio al agregar extras o complementos. | 
| Observaciones del pedido | El sistema deberá permitir ingresar observaciones especiales para cada producto solicitado. | 
| Detalles de Ordenes | El sistema deberá permitir agregar, modificar y eliminar productos antes de confirmar la orden. | 
| Generación de órdenes | El sistema deberá generar un número único para cada pedido registrado. | 
| Consulta de estado | El cliente deberá poder consultar el estado de su pedido en cualquier momento. | 
| Gestión de estados | El sistema deberá manejar los estados: Recibido, En preparación, Listo, Entregado y Cancelado. | 
| Actualización en tiempo real | El sistema deberá reflejar cambios de estado inmediatamente para clientes y colaboradores. | 
| Gestión de comandas | El personal de cocina deberá visualizar las órdenes pendientes ordenadas por prioridad o tiempo de ingreso. | 
| Cambio de estado por cocina | El personal de cocina deberá poder actualizar el estado de las órdenes. | 
| Visualización de observaciones | La cocina deberá visualizar notas especiales asociadas a cada pedido. | 
| Registro de pagos | El sistema deberá registrar los pagos asociados a los pedidos. | 
| Métodos de pago | El sistema deberá aceptar pagos en efectivo, tarjeta y SINPE Móvil. | 
| Pedidos para recoger | El sistema deberá mostrar el número de orden cuando el pedido esté listo para ser retirado. | 
| Autogestión de clientes | El sistema deberá permitir que los clientes realicen pedidos de manera autónoma. | 
| Gestión de usuarios | El sistema deberá administrar usuarios según roles definidos. | 
| Inicio de sesión | El sistema deberá permitir autenticación de usuarios mediante credenciales. | 
| Historial de pedidos | El sistema deberá almacenar el historial de pedidos realizados. | 
| Búsqueda de pedidos | El sistema deberá permitir buscar pedidos por número de orden, fecha, cliente o estado. | 
| Reportes administrativos | El sistema deberá generar reportes de ventas, pedidos y productos vendidos. | 
| Dashboard administrativo | El sistema deberá mostrar indicadores clave de gestión y operación. | 
| Notificaciones | El sistema deberá notificar al cliente cuando el pedido se encuentre listo. | 

## 2. Requerimientos No Funcionales

| Requerimiento No Funcional | Descripción | 
| ----- | ----- | 
| Usabilidad | La interfaz deberá ser intuitiva y fácil de utilizar para clientes y colaboradores. | 
| Rendimiento | El sistema deberá responder a las solicitudes del usuario lo más rapido posible | 
| Disponibilidad | El sistema deberá mantener una disponibilidad mínima del 99% durante el horario de servicio. | 
| Seguridad de acceso | Los usuarios deberán autenticarse mediante credenciales válidas. | 
| Protección de datos | La información de usuarios, pedidos y pagos deberá almacenarse de forma segura. | 
| Control de permisos | Cada rol deberá acceder únicamente a las funcionalidades autorizadas. | 
| Escalabilidad | El sistema deberá soportar un aumento de usuarios y pedidos sin afectar significativamente su desempeño. | 
| Compatibilidad de navegadores | El sistema deberá funcionar correctamente en Chrome, Edge, Firefox y Safari. | 
| Compatibilidad móvil | El sistema deberá ser responsive y funcionar en dispositivos móviles y tabletas. | 
| Integridad de datos | El sistema deberá garantizar la consistencia y exactitud de la información almacenada. | 
| Mantenibilidad | La solución deberá desarrollarse de forma modular para facilitar futuras mejoras. | 
| Respaldo de información | El sistema deberá realizar copias de seguridad periódicas de la base de datos. | 
| Auditoría | El sistema deberá registrar acciones relevantes realizadas por los usuarios. | 
| Accesibilidad | La interfaz deberá cumplir criterios básicos de accesibilidad visual y de navegación. | 
| Confiabilidad | El sistema deberá evitar la pérdida de información ante fallos inesperados. | 
| Actualización de estados | Los cambios de estado deberán reflejarse en un máximo de 5 segundos. | 
| Concurrencia | El sistema deberá soportar al menos 50 usuarios concurrentes. | 
| Tiempo de generación de reportes | Los reportes deberán generarse en menos de 10 segundos para consultas históricas. | 
| Portabilidad | El sistema deberá poder desplegarse en servidores locales o en la nube. | 
| Recuperación ante fallos | El sistema deberá permitir restaurar la información desde respaldos en caso de incidente. | 