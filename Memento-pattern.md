# MEMENTO PATTERN

## 1. Overview
Algunas veces es necesario guardar el estado de un objeto, por ejemplo, para implementar puntos de comprobación o el mecanismo de deshacer o recuperación de errores. Pero los objetos normalmente encapsulan algo o todo de su estado, haciendo este inaccesible a otros objetos e imposible guardarlo de forma externa. Exponer su estado viola la encapsulación, con la cual compromete la aplicación.

Este patrón puede ser usado para lograr esto sin exponer la estructura interna del objeto, el objeto cuyo estado necesita ser capturado se refiere como el originator.
La intención del patrón Memento es, sin violar la encapsulación, capturar y exteriorizar el estado interno de un objeto de forma que el objeto pueda ser restaurado a este estado después.

## 2. Participantes
* Memento (Recuerdo): Almacena el estado interno del objeto Originator. Memento puede almacenar tanto o tan poco del estado interno del Originator según sea necesario a criterio del autor.	Protege contra el acceso de objetos que no sean el Originator. Memento tiene dos interfaces. Caretaker ve una interfaz estrecha de	Memento, que solo puede pasar Memento de otros objetos. Originator, por el contrario, ve una gran interfaz, uno que le permite acceder a todos los datos necesarios para restaurarse a sí mismo a su estado anterior. Idealmente, solo el Originator que produjo el memento tiene permitido acceder al estado interno del memento.
** Originator (Autor): 	Crea un memento que contiene una instantánea de su estado interno actual. Usa el memento para restaurar su estado interno.
** Caretaker (vigilante): Es el responsable de la custodia del memento. Nunca opera sobre o examina el contenido de un memento.

Cuando un cliente quiere guardar el estado de un originator, hace una petición sobre el estado actual al originator. El originator almacena todos aquellos atributos que son requeridos para la restauración de su estado en un objeto independiente al que se refiere como Memento y lo devuelve al cliente. Así, un memento puede ser visto como un objeto que contiene el estado interno de otro objeto, en un punto dado del tiempo.
Un objeto Memento debe ocultar los valores de las variables de su Originator de todos los objetos excepto del Originator que lo creo. 

## 3. Cuando usar el patrón
* Para crear una instantánea del estado de un objeto que debe guardarse de manera que se pueda restaurar a ese estado después


![](http://www.dofactory.com/images/diagrams/net/memento.gif)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/memento)