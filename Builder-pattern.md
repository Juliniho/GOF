# BUILDER PATTERN

## 1. Overview
Utilizando el patrón builder, el proceso de construcción de un objeto se puede diseñar de manera más eficaz. Eeste patron sugiere mover la lógica de construcción de la clase de objeto a una clase aparte, contemplada como un generador de clases.
Buscando separar la construcción de un objeto complejo de su representación, de manera que el mismo proceso de construcción sea capaz de crear diferentes representaciones. Puede existir más de un objeto constructor, cada uno con diferentes implementaciones para la serie de pasos que se necesitan para construir el objeto. Con esto, el tamaño del objeto se reduce, el diseño resulta ser más modular con cada aplicación contenida en un objeto constructor diferente y la adición de una nueva aplicación (un constructor) se vuelve más fácil. 

En términos de implementación, cada uno de los diferentes pasos del proceso de construcción se pueden declarar como métodos de una interfaz común que sean implementados por diferentes constructores concretos. Un objeto cliente puede crear una instancia de un constructor concreto e invocar al conjunto de métodos requeridos para construir diferentes partes del objeto final. Este enfoque requiere que cada objeto cliente sea consciente de la lógica de la construcción. Cuando la lógica de construcción sufra un cambio, todos los objetos cliente necesitarán ser modificados en consecuencia.
 
El patrón Builder introduce un nivel de separación que aborda este problema. En lugar de tener objetos clientes que invoquen directamente diferentes constructores, el patrón sugiere el uso de un objeto específico referido como Director, que es responsable de la invocación de los diferentes métodos de construcción necesarios para la construcción del objeto final. Diferentes objetos cliente pueden hacer uso del objeto Director para crear el objeto requerido. Una vez construido el objeto, el objeto cliente puede solicitar directamente al constructor, el objeto totalmente construido. Para facilitar este proceso, un nuevo método getObject puede ser declarado en la interfaz común Builder que será la implementada por diferentes ConcreteBuilders.

## 2. Participantes
* Builder: Especifica una interfaz para la creación de partes de un objeto Product.
* Concrete Builder: Construye y ensambla las piezas del producto mediante la implementación de la interfaz Builder. Define y realiza un seguimiento de la representación que crea. Proporciona una interfaz para recuperar el producto.
* Director: Construye un objeto utilizando la interfaz del constructor.
* Producto: Representa el objeto complejo en su construcción. ConcreteBuilder construye una representación interna del producto y define el proceso por el cual se monta. Incluye clases que definen las partes constituyentes, incluyendo interfaces para el montaje de las partes en el resultado final.

## 3. Cuando usar el patrón
* Cuando el algoritmo de creación de un objeto complejo deba ser independiente para las partes que componen el objeto y la forma en la que son ensambladas
* El proceso de construcción deba permitir diferentes representaciones para el objeto que se está construyendo.


![](https://upload.wikimedia.org/wikipedia/commons/f/f3/Builder_UML_class_diagram.svg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/creational/builder)