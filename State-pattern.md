# STATEPATTERN

## 1. Overview
El patrón State permite que un objeto modifique su comportamiento cuando cambia su estado interno. El estado de un objeto se puede definir como su condición exacta en cualquier punto del tiempo, dependiendo de los valores de sus propiedades. El conjunto de métodos implementados por la clase constituye el comportamiento de las instancias. Cada vez que hay un cambio en el valor de sus atributos, se dice que el estado de un objeto ha cambiado.

El patrón State es útil en el diseño eficiente de la estructura para una clase, una instancia típica de las cuales puede existir varios estados diferentes y muestra un comportamiento diferente en función del estado en que se encuentra. En otras palabras, en el caso de un objeto de tal clase, algunos o todos de sus comportamientos están influenciados por el estado actual del objeto. En la terminología del patrón State, una clase de este tipo se denomina una clase de contexto. Un objeto de contexto puede alterar su comportamiento cuando hay un cambio en su estado interno y también se conoce como un objeto con estado.

El patrón State sugiere mover los estados específicos de comportamiento fuera de la clase de contexto a un conjunto 
de clases separadas referidas como clases estado. Cada uno de los muchos diferentes estados que pueden existir en el objeto contexto pueden estar mapeados en una clase estado separada. La implementación de la clase estado contiene el comportamiento del contexto que es especifico dado un estado, no el comportamiento del contexto en general.
El contexto actúa como un cliente para el conjunto de objetos estados en el sentido que hace uso de diferentes objetos del estado para ofrecer el comportamiento especifico de estado necesario para un objeto de la aplicación que utiliza el contexto de una manera transparente.

La encapsulación del comportamiento especifico del estado en clases separadas, implementación del contexto, se hace más simple para leer: sin demasiados estados condicionales como son if-else o switch-case. Cuando un objeto contexto es creado por primera vez, este se inicializa a si mismo con su objeto estado inicial. Este objeto state se convierte en el objeto estado actual del contexto. Al reemplazar el objeto estado actual con un nuevo objeto estado, el contexto se mueve a un nuevo estado.

La aplicación cliente que usa el contexto no es responsable de especificar el objeto estado actual para el contexto, pero en cambio, se espera, que cada una de las clases estado representen un estado específico para proporcionar la implementación necesaria para moverse a la siguiente transición de estado. Cuando un objeto de aplicación hace una llamada al método de contexto(comportamiento), este reenvía la llamada al objeto estado actual.

## 2. Participantes
 * Context: Define la interfaz de interés para los clientes. Mantiene una instancia de una subclase ConcreteState que define el estado actual.
* State: Define una interfaz para encapsular el comportamiento asociado con un estado particular del estado.
* ConcreteState: Cada subclase implementa un comportamiento asociado con un estado del contexto.	

## 3. Cuando usar el patrón
 * Cuando el comportamiento de un objeto dependa de su estado, y deba de cambiar su comportamiento en tiempo de ejecución dependiendo de su estado
 * Cuando existan operaciones que tengan sentencias condiciones grandes, de varias partes que dependen del estado del objeto.	Este estado sea usualmente representado por uno o más constantes enumeradas. A menudo, varias operaciones contendrán esta	misma estructura condicional. El patrón State pone en cada rama condiciona una subclase separada. Esto le permite tratar el estado del objeto como un objeto en sí mismo, que puede variar dependiendo de otros objetos.


![](https://upload.wikimedia.org/wikipedia/commons/e/e8/State_Design_Pattern_UML_Class_Diagram.svg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/state)