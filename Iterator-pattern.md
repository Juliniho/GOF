# ITERATOR PATTERN

## 1. Overview
Colecciones, como una lista, deben dar la posibilidad de acceder a sus elementos sin exponer su estructura interna. Por otra parte, es posible que se desee recorrer la lista de diferentes maneras, dependiendo de lo que se 
quiera lograr. Pero es probable que no quiera añadir metodos de mas a la interfaz del List con diferentes operaciones transversales, incluso si se pudiera anticipar los que se necesitan. Esto permite hacer este patrón.
La idea clave de dicho patrón es tomar la responsabilidad del acceso y recorrido fuera del objeto lista y ponerla en un objeto iterator. La clase iterator define una interfaz para acceder a los elementos de la lista. Un objeto iterator es
responsable de hacer el seguimiento del elemento actual, es decir, saber que elementos a recorrido ya.

La intención del patrón Iterator es proporciona una forma de acceder a los elementos de un objeto agregado secuencialmente sin exponer su representación subyacente. Este patrón permite a un objeto cliente acceder al contenido de una lista sin
tener ningún conocimiento acerca de la representación interna de los datos. Para permitir esto, el objeto iterador debe proporcionar una interfaz publica para diferentes objetos contenidos.

## 2. Participantes
 * Iterator: Define la interfaz para acceder y recorrer los elementos
* ConcreteIterator: Implementa la interfaz Iterator, realiza el seguimiento de la posición actual en el recorrido del contenedor.
* Aggregate: Define la interfaz para crear un objeto Iterator
* ConcreteAggregate: Implementa la interfaz de creación del Iterator para devolver una instancia adecuada del iterator
	
## 3. Iteradores Internos y Externos
### 3.1 - Internos:
La colección en si ofrece métodos que permiten al cliente obtener diferentes objetos dentro de la colección. Como puede ser ResultSet, que contiene los datos y ofrece métodos como next. Solo puede existir un iterador por colección en un momento dado. La colección tiene que mantener o guardar el estado de la iteración.
### 3.2 - Externos:
La funcionalidad del iterador está separado de la colección y se guarda dentro del objeto referido como iterator. Por lo general, la propia colección devuelve el objeto apropiado de iterator al cliente dependiente de la entrada del cliente.	Por ejemplo, java.util.Vector tiene su iterador externo de tipo Enumeration. Pueden existir varios iterators para una colección en un momento dado. La sobrecarga implica que el almacenamiento del estado del iterator no esté asociada a la colección, se encuentra en el objeto iterador exclusivamente.

## 4. Cuando usar el patrón
* Cuando se quiera acceder al contenido de un objeto agregado sin exponer su representación interna
* Para dar soporte a múltiples recorridos de objetos agregados
* Para proporcionar un interfaz uniforme para recorrer diferentes estructuras (dar soporte a la iteración polimórfica)

![](https://upload.wikimedia.org/wikipedia/commons/5/53/Ejemplo_patr%C3%B3n_iterador_2.png)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/iterator)