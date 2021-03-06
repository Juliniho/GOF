# OBSERVER PATTERN

## 1. Overview
Es un tipo de patrón de comportamiento, que se refiere a la asignación de responsabilidades entre los objetos.
El patrón Observer, también conocido como el patrón de publicación-inscripción, define una dependencia de uno a muchos entre los objetos de manera que cuando un objeto cambia de estado, todos sus dependientes son notificados y se actualizan automáticamente. El patrón Observer describe estas dependencias. Los objetos clave en este modelo son sujeto y observer. 
Un sujeto puede tener cualquier número de observadores dependientes. Todos los observadores son notificados cada vez que el sujeto sufre un cambio en su estado. En respuesta, cada observador consultará el objeto para sincronizar su estado con el estado del sujeto. El patrón Observer es la clave del patrón de arquitectura Modelo Vista Controlador (MVC).

## 2. Participantes
* Sujeto: interfaz usada para registrar y/o eliminar observadores.
* Observador: define la interfaz de actualización para los objetos que debes ser notificados de cambios en el sujeto. Todos los observadores implementan la interfaz Observer.
* ConcreteSubjet: almacena el estado de interés para los ConcreteObserver. Él es encargado de enviar la notificación al producirse un cambio. Siempre implementa el interfaz sujeto. 
* ConcreteObserver: mantiene una referencia a un objeto ConcreteSubject e implementa la interfaz Observer. Cada observer se registra con un sujeto concreto para recibir las notificaciones.
	
## 3. Cuando usar el patrón
* Cuando una abstracción tiene dos aspectos y una depende de otra. La encapsulación de estos aspectos en objetos separados le permite varias y volver a utilizarlos de forma independiente.
* Cuando un cambio en un objeto requiere cambios en otros objetos y no se conoce el núm. de objetos a cambiar, así como, se quiere conseguir un desacoplamiento entre todos los objetos.


![](https://upload.wikimedia.org/wikipedia/commons/9/97/EstructuraPatronObservador.png)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/observer)