# VISITOR PATTERN

## 1. Overview
Este patrón le proporciona una forma de añadir nuevos operadores a los objetos sin cambiar las clases de los elementos, especialmente cuando las operaciones cambian con bastante frecuencia. La intención de este patrón es representar una operación a realizar sobre los elementos de una estructura de objetos.
Visitor permite definir nuevas operaciones sin cambiar las clases de los elementos sobre los que se opera. Este patrón es útil cuando se diseña de una operación a través de una colección heterogénea de objetos de una jerarquía de clases. El patrón permite a las operaciones ser definidas sin cambiar la clase de cualquiera de los objetos de la colección. Para logar esto, se define el funcionamiento en una clase separada a la que se hace referencia con una clase visitor. Esto separa la operación de la colección de objetos sobre la que actúa. Por cada nueva operación definida, una nueva clase visitor es creada. Dada que la operación se va a realizar a través de un conjunto de objetos, el visitor necesita
una forma de acceder a los miembros públicos de estos objetos.


## 2. Participantes
* Visitor: Declara una operación de Visit para cada clase ConcreteElement en la estructura de objetos. El nombre y la firma identifica la case que envía la petición Visit sobre el visitor. Esto permite que el visitor determine una clase concreta de los elementos que han sido visitados. Entonces el visitor puede acceder al elemento directamente a través de su interfaz particular.
* ConcreteVisitor: Implementa cada operación declarada por el Visitor. Cada operación implementa un fragmento del algoritmo definido por la clase correspondiente del objeto en la estructura. Proporciona el contexto para el algoritmo y almacena su estado local. Este estado acumula a menudo los resultados durante el recorrido de la estructura.
* Element: Define una operación Accept que toma un visitor como un argumento.
* ConcreteElement: Implementa una operación Accept que toma el visitor como argumento.
* ObjectStructure: Enumera sus elementos. Puede proporcionar un interfaz de alto nivel que permite al visitor visitar sus elementos. Puede ser compuesto o una colección como un list o un set.

## 3. Cuando usar el patrón
* Una estructura de objetos contiene muchas clases de objetos con diferentes interfaces y se desea realizar operaciones sobre estos objetos que dependen de sus clases concretas.
* Muchas operaciones distintas y no relacionadas deben ser aplicadas a objetos en una estructura de objetos y se quieren evitar "contaminar" sus clases con estas operaciones. Visitor permite mantener las operaciones relacionadas entre sí definiéndolas en una clase. Cuando el objeto estructura es compartido por muchas aplicaciones, el uso de Visitor permite poner estas operaciones en solo aquellas aplicaciones que lo necesiten.
* Las clases que definen la estructura de objetos rara vez cambian, pero a menudo se quiere definir nuevas operaciones sobre la estructura. Cambiando la clase del objeto estructura se requiere redefinir la interfaz para todos los visitor, lo cual es potencialmente costoso. Si las clases de estructura de objetos cambian con frecuencia, entonces probablemente será mejor cambiar la definición de las operaciones en las otras clases.
	

![](http://www.dofactory.com/images/diagrams/net/visitor.gif)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/visitor)