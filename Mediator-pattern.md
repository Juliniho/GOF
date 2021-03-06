# MEDIATOR PATTERN

## 1. Overview
Este patrón define un objeto que encapsula a un conjunto de objetos que interactúan entre si. El mediador fomenta un acoplamiento débil manteniendo objetos que se refieren a otros objetos explícitamente y que le permite variar su interacción con independencia.
En vez de interactuar directamente entre sí, los objetos piden al mediador que actué en su nombre dando como resultado reusabilidad y bajo acoplamiento. El mediador encapsula la interacción entre objetos y los hace independientes los unos de los otros. Esto les permite variar su interacción con otros objetos de una manera totalmente diferente mediante la implementación de un mediador diferente. El mediador ayuda a reducir la complejidad de las clases. Cada objeto ya no tiene que conocer en detalle acerca de cómo interactuar con los demás objetos.
El uso de este patrón permite que el código de interacción resida en un solo lugar, haciéndolo mas fácil de mantener.

## 2. Participantes
* Mediator: Define la interfaz para comunicarse con objetos Colleague.
* ConcreteMediator: Implementa el comportamiento cooperativo para coordinar los objetos Colleague. También conoce y mantiene los Colleagues
* Colleague: Cada clase de este tipo conoce a su objeto Mediator y se comunica con él.

## 3. Cuando usar el patrón
* Cuando la comunicación de un conjunto de objetos este bien definida, pero sea muy compleja con interdependencias sin estructura y difíciles de entender.
* La reutilización de un objeto sea difícil porque se refiere y se comunica con muchos otros objetos.
* Un comportamiento que se distribuye entre varias clases debe ser adaptable sin una gran cantidad de subclases.

![](http://www.dofactory.com/images/diagrams/net/mediator.gif)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/mediator)