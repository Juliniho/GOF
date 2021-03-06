# ABSTRACT FACTORY PATTERN

## 1. Overview
Este es un patrón de diseño que proporciona una interfaz para crear familias de objetos relacionados o dependientes sin especificar sus clases concretas. El patrón Abstract Factory lleva el concepto del patrón Factory Method al siguiente nivel. Un factory abstracto es una clase que proporciona una interfaz para producir una familia de objetos. En Java, 
se puede implementar usando una interfaz o una clase abstracta.
El patrón Abstract Factory es útil cuando un cliente quiere crear una instancia de un conjunto de clases relacionadas, dependientes sin tener que saber qué clase especifica en concreto debe crear la instancia. Diferentes factories concretas implementan la interfaz factory abstracta. Los clientes hacen uso de estas factories para crear objetos y, por lo tanto, no es necesario saber qué clase concreta está actualmente instanciada.

El factory abstract es útil para la conexión de un grupo diferente de objetos para alterar el comportamiento del sistema. Para cada grupo o familia, una concretefactory es implementada para manejar la creación de objetos y la interdepencia y los requisitos de consistencia entre ellos. Cada implementación concreta implementa la interfaz de la factory abstracta.

## 2. Participantes
* AbstractFactory: Declara una interfaz para operaciones de productos que crean objetos abstractos
* ConcreteFactory: Implementa las operaciones para crear objetos de productos concretos.
* AbstractProduct: Declara la interfaz para un tipo de producto objeto.
* ConcreteProduct: Define un objeto de producto que se va a crear por la factoría correspondiente. Implementa una interfaz AbstractProduct
* Client: Usa solo la interfaz declarada por AbstractFactory y AbstractProduct
	
## 3. Cuando usar el patrón
* Cuando un sistema deba ser independiente de la forma en la que se crean sus productos, se componen o se representan.
* Cuando un sistema deba ser configurado con múltiples familias de productos.
* Cuando se desee proporcionar una biblioteca de clases de productos y quiera solo exponer las interfaces y no sus implementaciones

![](http://www.dofactory.com/images/diagrams/net/abstract.gif)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/creational/abstractfactory)