# PROTOTYPE PATTERN

## 1. Overview
A grandes rasgos, ayuda en la creación de objetos pesados en construccion, ya que crea uno y luego lo copia.

El patrón prototype  se usa para especificar los tipos de objetos que se crearan usando una instancia prototípica y crear nuevos objetos copiando este prototipo. El concepto consiste en copiar un objeto existente en lugar de crear una nueva instancia desde cero (la cual incluye operaciones costosas). El objeto existente actúa como prototipo y contiene el estado del objeto. El nuevo objeto copia puede cambiar alguna de sus propiedades solo si es necesario. Este método ahorra recursos costosos y tiempo, especialmente cuando la creación de objetos es muy pesada.

En Java, hay ciertas formas de copiar un objeto con el fin de crear uno nuevo. Una forma de lograr esto es usar la interfaz Cloneable. Java provee el método clone, heredado de la clase Objects. Tu necesitas implementar la interfaz Clonable y sobreescribir el método clone de acuerdo a tus necesidades.


## 2. Participantes
* Prototype: Declara la interfaz que se podrá clonar
* ConcretePrototype: Implementa una operacion para la clonación en si.
* Client: Crea un nuevo objeto al preguntar a prototype para clonar en si.	

Los prototipos permiten incorporar nuevas clases de productos concretos en un sistema mediante el simple registro de una instancia prototípica con el cliente.


## 3. Cuando usar el patrón
* Use  el patrón prototipo cuando un sistema deba ser independiente de la forma	en que sus productos son creados, compuestos y representados.
* Cuando las clases a instanciar se especifiquen en tiempo de ejecución, por ejemplo, para la carga dinámica.
* Cuando instancias de una clase puedan tener un solo estado de unos pocos diferentes. Puede que sea mas conveniente instanciar un número correspondiente de prototipos y clonarlos en lugar de crear las instancias de la clase de forma manual cada vez con el estado apropiado.

![](http://www.dofactory.com/images/diagrams/net/prototype.gif)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/creational/prototype)