# DECORATOR PATTERN

## 1. Overview
La intención del patrón Decorator es unir responsabilidades adicionales a un objeto de forma dinámica. Decorator proporciona una alternativa flexible a las sub clases para extender funcionalidad. El patrón decorador se utiliza para extender funcionalidad a un objeto de forma dinámica sin tener que cambiar el código fuente original o usar herencia. Esto se logra mediante la creación de una envoltura del objeto, referida como Decorator. Más flexible que la herencia. Al utilizar este patrón, se pueden añadir y eliminar responsabilidades en tiempo de ejecución. Además, evita la utilización de la herencia con muchas clases y también, en algunos casos, la herencia múltiple. Evita la aparición de clases con muchas responsabilidades en las clases superiores de la jerarquía. Este patrón nos permite ir incorporando de manera incremental responsabilidades. Genera gran cantidad de objetos pequeños. El uso de decoradores da como resultado sistemas formados por muchos objetos pequeños y parecidos.
 
El objeto Decorator está diseñado para tener la misma interfaz que el objeto subyacente. Esto permite al cliente interactuar con el objeto decorator exactamente de la misma manera que lo haría con el objeto real. El objeto decorator contiene una referencia al objeto real. El objeto decorator recibe todas las peticiones de un cliente. A su vez reenvía estas llamadas al objeto subyacente. El objeto del decorador añade algunas funciones adicionales antes o después
de reenviar solicitudes al objeto subyacente. Esto asegura que la funcionalidad adicional se puede añadir a un objeto dado externamente en tiempo de ejecución sin modificar su estructura.
 
Decorator evita la proliferación de subclases que conducen a una menor complejidad y confusión. Es fácil agregar cualquier combinación de capacidades. Las mismas capacidades pueden incluso añadirse dos veces. Es posible tener en un momento dado diferentes objetos Decorator para el mismo objeto. Un cliente puede elegir que capacidades quiere para enviar el mensaje
hacia el decodator apropiado.

## 2. Participantes
* Component: Define la interfaz para los objetos que puede tener responsabilidades añadidas de forma dinámica
* ConcreteComponent: Define un objeto para las responsabilidades añadidas  
* Decorator: Mantiene una referencia a un Component y define la interfaz que ajusta la interfaz del Component
* ConcreteDecorator: Añade las responsabilidades al componente

## 3. Cuando usar el patrón
* Cuando se quiera añadir responsabilidades a los objetos individuales de forma dinámica y transparente.
* Cuando la extensión por sub-clases es poco práctica. A veces, son posibles un gran numero de extensiones independientes y produciría una explosión de subclases para apoyar cada combinación. 

![](https://upload.wikimedia.org/wikipedia/commons/e/e9/Decorator_UML_class_diagram.svg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/structural/decorator)