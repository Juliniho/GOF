1. Behavioral
   + 1.01 [Chain Responsibility](https://github.com/ajpaez/Learning/wiki/Chain-Responsibility)
   + 1.02 [Command](https://github.com/ajpaez/Learning/wiki/Command)
   + 1.03 [Interpreter] (https://github.com/ajpaez/Learning/wiki/Interpreter-pattern)
   + 1.04 [Iterator] (https://github.com/ajpaez/Learning/wiki/Iterator-pattern)
   + 1.05 [Mediator] (https://github.com/ajpaez/Learning/wiki/Mediator-pattern)
   + 1.06 [Memento] (https://github.com/ajpaez/Learning/wiki/Memento-pattern)
   + 1.07 [Observer] (https://github.com/ajpaez/Learning/wiki/Observer-pattern)
   + 1.08 [State] (https://github.com/ajpaez/Learning/wiki/State-pattern)
   + 1.09 [Strategy] (https://github.com/ajpaez/Learning/wiki/Strategy-pattern)
   + 1.10 [Template] (https://github.com/ajpaez/Learning/wiki/Template-Method-pattern)
   + 1.11 [Visitor] (https://github.com/ajpaez/Learning/wiki/Visitor-pattern)

2. Creational
   + 2.01 [Abstract Factory](https://github.com/ajpaez/OCA/wiki/2.1-Encapsulaci%C3%B3n)
   + 2.02 [Builder](https://github.com/ajpaez/OCA/wiki/2.2-Herencia-y-polimorfismo)
   + 2.03 [Factory method] (https://github.com/ajpaez/OCA/wiki/2.3-Polimorfismo)
   + 2.04 [Prototype] (https://github.com/ajpaez/OCA/wiki/2.4-Overriding-Overloading)
   + 2.05 [Singleton] (https://github.com/ajpaez/OCA/wiki/2.5-Casting)

3. Structural
   + 3.01 [Adapter](https://github.com/ajpaez/OCA/wiki/3.1-El-Stack-y-el-Heap)
   + 3.02 [Bridge](https://github.com/ajpaez/OCA/wiki/3.2-Literales,-asignaciones-y-variables)
   + 3.03 [Composite] (https://github.com/ajpaez/OCA/wiki/3.3-Scope)
   + 3.04 [Decorator] (https://github.com/ajpaez/OCA/wiki/3.4-Inicializaci%C3%B3n-de-variables)
   + 3.05 [Flyweight] (https://github.com/ajpaez/OCA/wiki/3.5-Paso-de-variables-a-m%C3%A9todos)
   + 3.06 [Proxy] (https://github.com/ajpaez/OCA/wiki/3.6-Recolector-de-basura)

4. Architecture
   + 4.1 [DAO](https://github.com/ajpaez/OCA/wiki/3.3-Scope)


> Fuente: 	https://www.javacodegeeks.com/2015/09/java-design-patterns.html

# 1. Categorización de patrones

##1.1  - Patrones de creación
Son usados para diseñar el proceso de instanciación de objetos. Un patrón creacional usa la herencia para variar la creación de objetos.
Todos ellos encapsulan el conocimiento sobre que clases concretas usa el sistema y ocultan la creación y puesta en común de todas las instancias de estas clases.
Todo el sistema tiene conocimiento en general es sus interfaces según están definidas en clases abstractas.
En consecuencia, estos patrones aportan gran flexibilidad en lo que se creó, quien lo creó, como se creó y cuando.

> Abstract Factory;Builder;Factory Method;Prototype;Singleton

##1.2 - Patrones estructurales
Estos patrones de refieren a como las clases y objetos se componen para formar estructuras más grandes.
Los patrones estructurales de clase usan la herencia para componer interfaces o implementaciones, como puede ser la herencia múltiple, al mezclar dos o más clases en una,el resultado es una clase que combina las propiedades de sus clases padre. Este patrón es particularmente útil para hacer bibliotecas de clases desarrollados independientemente para que trabajen juntas.
En lugar de preparar las interfaces o implementaciones, los patrones de objetos estructurales describen las maneras de componen objetos para darse cuenta de la nueva funcionalidad.
La flexibilidad de la composición del objeto proviene de la capacidad de cambiar la composición en tiempo de ejecución, lo cual es imposible con la composición de clases estáticas.

> Adapter;Builder;Composite;Decorator;Façade;Flyweight;Proxy

##1.3 - Patrones de comportamiento
Los patrones de comportamiento se refieren a los algoritmos y a la asignación de responsabilidades entre objetos. Estos patrones no solo describen los patrones de los objetos o clases, sino también los patrones de comunicación entre ellos. Estos patrones caracterizan el flujo de control complejo difícil de seguir en tiempo de ejecución. En estos patrones se usa la composición de objetos en lugar de la herencia.  Algunos describen cómo un grupo de objetos pares cooperan para realizar una tarea que ningún objeto solo puede llevar a cabo por sí mismo.
Para evitar el acoplamiento entre objetos, por el traspaso de información, se define la figura del mediador que es el encargado de proporcionar el direccionamiento indirecto necesario para la perder dicho acoplamiento.

> ChainofResponsibility;Command;Interpreter;Iterator;Mediator;Memento;Observer;State;Strategy;Template Method;Visitor

##1.4 - Patrones de arquitectura
Un patrón de arquitectura es una solución general y reutilizable a un problema que ocurre comúnmente en arquitectura de software dentro de un contexto dado. Los patrones arquitectónicos son similares a los patrones de diseño de software, pero tienen un alcance más amplio. Los patrones arquitectónicos abordar diversas cuestiones en la ingeniería de software, tales como las limitaciones de rendimiento de hardware de computadora, la alta disponibilidad y la reducción al mínimo de los riesgos empresariales. 
Algunos patrones arquitectónicos se han implementado dentro de framworks. A pesar de que un patrón arquitectónico transmite una imagen de un sistema, no es una arquitectura. 
Un patrón de arquitectura es un concepto que resuelve y esboza algunos elementos de cohesión esenciales en una arquitectura de software. Innumerables arquitecturas diferentes pueden aplicar el mismo patrón y compartir las características relacionadas. Los patrones se definen a menudo como "estrictamente descrito y comúnmente disponible".Cuando son descritos estrictamente y comúnmente disponibles, son un patrón.


| Creational Patterns  | Structural Patterns  |  Behavioral Patterns |
|---|---|---|
| Abstract Factory  | Adapter  | Chain of Responsibility  |
|  Builder | Bridge |  Command |	
| Factory Method  | Composite  | Interpreter  |	
| Prototype  | Decorator  | Iterator  |	
| Singleton  |  Façade | Mediator  |	
|   | Flyweight  |  Memento |	
|   |  Proxy |  Observer |	
|   |   | State  |	
|   |   |  Strategy |	
|   |   | Template Method  |	
|   |   | Visitor  |

											