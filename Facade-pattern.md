# FACADE  PATTERN

## 1. Overview
El patrón de diseño estructural facade hace una interfaz compleja más fácil de usar, utilizando una clase Facade. El patrón proporciona una interfaz unificada a un conjunto de interface en un subsistema. Facade define una interfaz de alto nivel que hace que el subsistema sea más fácil de usar. Simplemente proporciona una capa para las interfaces complejas del subsistema que hace que sea más fácil de usar. Facade no encapsula clases o interfaces del sistema, sólo proporciona una interfaz simplificada para su funcionalidad. Un cliente puede acceder a estas clases directamente, todavía expone la 
funcionalidad completa del sistema para los clientes que lo necesiten. 

Facade no es solo capaz de simplificar una interfaz, sino que también desacopla a un cliente de un subsistema. Para ello, se adhiere al [principio del menor conocimiento] (https://es.wikipedia.org/wiki/Ley_de_Demeter) , evitando así, el acoplamiento producido entre un cliente y el subsistema y proporcionando flexibilidad.
Los clientes se comunican con el subsistema mediante el envío de solicitudes a Facade, que los reenvía al objeto(s) apropiados del subsistema. A pesar de que los objetos del subsistema realizan el trabajo real, facade puede tener que hacer el trabajo de su propia traducción a las interfaces del subsistema.

Tenga en cuenta que Facade al igual que Adapter puede envolver varias clases, pero Facade utiliza una interfaz para simplificar el uso de interfaces complejas, mientras que adapter se usa para convertir una interfaz en la interfaz esperada por el cliente.

Facade es usado cuando se desea una interfaz mas fácil para el objeto subyacente. Alternativamente, adapter se puede utilizar cuando la envoltura debe respetar una interfaz en particular y debe soportar comportamiento polimorfico. El decorator hace que sea posible añadir o alterar el comportamiento de una interfaz en tiempo de ejecución. 

| Patrón  | Objetivo|
|---|---|
| Adapter  | Convertir una interfaz en otra para que coincida con lo que el cliente está esperando  |
| Decorator  |  Añadir dinámicamente funcionalidad a la interfaz envolviendo el código original |
| Facade  | Proporcionar una interfaz simple  |

## 2. Participantes
* Facade: conoce qué clases del subsistema son responsables de una determinada petición, y delega esas peticiones de los clientes a los objetos apropiados del subsistema.
* Subclases (ModuleA, ModuleB, ModuleC...): implementan la funcionalidad del subsistema. Realizan el trabajo solicitado por la fachada. No conocen la existencia de la fachada.

## 3. Cuando usar el patrón
* Cuando se desee proporcionar una interfaz sencilla para un subsistema complejo, con él se puede proporcionar una vista predeterminada sencilla del subsistema que es lo suficientemente bueno para la mayoría de los clientes y solo los clientes que lo necesiten tiene la posibilidad de usar más allá de la fachada.
* Cuando existan muchas dependencias entre los clientes y las clases de implementación de una abstraccion, introducir una fachada desacopla los subsistemas de los clientes y el resto de subsistemas.
* Permite establecer mejor las capas en los subsistemas, utilizando Facade permite definir un punto de entrada en cada nivel de subsistema. Si los subsistemas son dependientes, entonces se puede simplificar la dependencia entre ellos haciéndolos que se comuniquen entre sí a través se sus fachadas.


![](https://upload.wikimedia.org/wikipedia/commons/d/d4/Facade_UML_class_diagram.svg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/structural/facade)
