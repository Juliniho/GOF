# FLYWEIGHT PATTERN

## 1. Overview
Este patrón está diseñado para controlar la creación de objetos que tienen grandes similitudes entre ellos y son de un tipo similar, lo que implica que la mayoría de sus propiedades tienen valores similares. Además, este patrón proporciona un mecanismo básico de almacenamiento en cache. Esto permite crear un objeto por tipo (se entiende por tipo a los objetos que tiene las mismas propiedades) cuando se solicite un objeto con las mismas propiedades (ya creado), se devuelva el mismo objeto en lugar de crear uno nuevo.
 
El objetivo de este patrón es utilizar objetos compartidos para soportar un gran número de objetos de baja granularidad (propiedades muy bien definidas y divididas)[https://en.wikipedia.org/wiki/Granularity#Data_granularity]. Un objeto flyweight es un objeto compartido que puede ser utilizado en múltiples contextos simultáneamente. Este objeto actúa como un objeto independiente en cada contexto, flyweight no puede hacer suposiciones sobre el contexto en el que opera. El concepto clave aquí es la distinción entre el estado intrínseco y extrínseco. El estado intrínseco es almacenado en el objeto flyweight, consiste en la información que es independiente de contexto del flyweight, con lo que se puede compartir. El estado extrínseco depende y varia con el contexto del objeto flyweight y por lo tanto no puede ser
compartida. Los objetos cliente son responsables de la transmisión del estado extrínseco al objeto flyweight cuando este lo necesita.

### 1.1 Inmutabilidad e igualdad
Para permitir el uso compartido seguro entre los clientes y los hilos, los objetos flyweight deben ser inmutables. Los objetos flyweight son por definición objetos de valor. La identidad de las instancias de los objetos no tiene ninguna consecuencia, por lo tanto, dos instancias de flyweight con los mismos valores se consideran iguales.

## 2. Participantes
* Flyweight: Declara la interfaz a través del cual flyweights puede recibir y actuar sobre el estado extrínseco
* ConcreteFlyweight: Implementa la interfaz Flyweight y añade almacenamiento para el estado intrínseco si los hubiere. Debe ser compatible. Cualquier estado almacenado debe ser intrínseco, es decir, independiente del contexto del propio objeto. 
* FlyweightFactory: Crea y administra objetos flyweight. Asegura que dichos objetos son compartidos. Cuando un cliente requiere uno de ellos, el objeto FlyweightFactory le suministra uno si existe sino lo crea
* Client: Mantiene una referencia al flyweight, calculo o almacena el estado extrínseco de estos objetos.	

## 3. Cuando usar el patrón
La aplicación del patrón depende en gran medida de cómo y dónde se utilice. Aplicar el patrón cuando todas las condiciones siguientes son true:
* Una aplicación use una gran numero de objetos.
* Los costes de almacenamiento son altos debidos a la gran cantidad de objetos.
* La mayor parte del estado del objeto puede ser extrínseca.
* Muchos objetos pueden ser reemplazado por relativamente pocos objetos compartidos una vez que se elimina el estado extrínseco. 


![](http://www.dofactory.com/images/diagrams/net/flyweight.gif)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/structural/flyweight)