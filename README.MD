Se desea ampliar la aplicación de comercio electrónico de la práctica 1 hecha en Java con Spring.
Concretamente, se desea poder consultar el valor de los carritos completados:
 • GET /cartexpenditure/ 
 [
  {cartId: 23, expenditure: 566},
  {cartId: 101, expenditure: 23}
 ]
 
Para ello, se incluirá en el carrito el precio total que deberá actualizarse cada vez que se añade unproducto al carrito.

Además, se ha decidido usar una arquitectura dirigida por eventos. Esta arquitectura se implementaráen dos pasos:
 • En un primer paso, cuando se cierre un carrito se debe notificar el evento de cierre de carrito y un servicio dentro de la misma aplicación se encargará de actualizar la vista de carritoscompletados (nótese que esta vista consiste en una tabla en la base de datos que contiene exclusivamente el id del carrito y el precio total resultado de sumar todos los productos). Se debe proporcionar también el controlador que muestra la lista de carritos cerrados con su gasto.
 
 • En un segundo paso se convertirá el resto de la aplicación a una arquitectura dirigida por eventos aplicando CQRS. Se separarán los controladores en comandos y consultas. Los comandos enviarán eventos que serán procesados para realizar los cambios pertinentes en el modelo y persistirlos.
 
Nota: La implementación de la tecnología de eventos se puede realizar usando eventos dentro de la aplicación Spring, utilizando la librería para eventos de RabbitMQ o utilizando Spring Cloud Stream.
En estos dos últimos casos será necesario disponer de un sistema de gestión de colas (preferiblemente RabbitMQ).

Se pide:
 • Un nuevo endpoint para mostrar la lista de carritos cerrados y su cantidad total (1 pt)
 • Actualización de dicha lista mediante eventos lanzados cuando se cierra el carrito (3 pts)
 • Separación del resto de endpoints en comandos y consultas usando el enfoque CQRS (2 pts)
 • Cambio de la implementación de los comandos a una arquitectura dirigida por eventos (4 pts)